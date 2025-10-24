
	#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Function to generate computer choice: 1 = Snake, 2 = Water, 3 = Gun
int generateRandomNumber()
{
    srand(time(NULL));
    return (rand() % 3) + 1;
}

// Function to decide winner
// Returns: 1 if you win, -1 if computer wins, 0 if draw
int gameLogic(int you, int comp)
{
    if (you == comp)
        return 0;

    // Snake vs Water or Gun
    if (you == 1 && comp == 2)
        return 1; // Snake drinks water -> You win
    else if (you == 1 && comp == 3)
        return -1; // Gun kills snake -> You lose

    // Water vs Snake or Gun
    else if (you == 2 && comp == 1)
        return -1; // Snake drinks water -> You lose
    else if (you == 2 && comp == 3)
        return 1; // Water damages gun -> You win

    // Gun vs Snake or Water
    else if (you == 3 && comp == 1)
        return 1; // Gun kills snake -> You win
    else if (you == 3 && comp == 2)
        return -1; // Water damages gun -> You lose

    return 0;
}

int main()
{
    int you, comp;
    int result;

    printf("\n===== 🐍💧🔫 Snake, Water, Gun Game =====\n");
    printf("Choose one:\n");
    printf("1. Snake\n");
    printf("2. Water\n");
    printf("3. Gun\n");
    printf("----------------------------------------\n");
    printf("Enter your choice (1/2/3): ");
    scanf("%d", &you);

    if (you < 1 || you > 3)
    {
        printf("❌ Invalid choice! Please enter 1, 2, or 3.\n");
        return 0;
    }

    comp = generateRandomNumber();

    printf("\nYou chose: ");
    if (you == 1)
        printf("Snake 🐍\n");
    else if (you == 2)
        printf("Water 💧\n");
    else
        printf("Gun 🔫\n");

    printf("Computer chose: ");
    if (comp == 1)
        printf("Snake 🐍\n");
    else if (comp == 2)
        printf("Water 💧\n");
    else
        printf("Gun 🔫\n");

    result = gameLogic(you, comp);

    printf("----------------------------------------\n");
    if (result == 0)
        printf("😐 It's a draw!\n");
    else if (result == 1)
        printf("🎉 You win!\n");
    else
        printf("💻 Computer wins!\n");

    printf("----------------------------------------\n");
    return 0;

        
