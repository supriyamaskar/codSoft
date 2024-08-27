# codSoft

package pro1codesoft;

	import java.util.Random;
	import java.util.Scanner;

	public class NumberGuessingGame {
	    public static void main(String[] args) {
	        Scanner scanner = new Scanner(System.in);
	        Random random = new Random();
	        boolean playAgain = true;
	        int score = 0;
	        int round = 1;
	        int maxAttempts = 5; // You can set the maximum number of attempts

	        while (playAgain) {
	            System.out.println("Round " + round);
	            int numberToGuess = random.nextInt(100) + 1; // Generate random number between 1 and 100
	            int attempts = 0;
	            boolean hasGuessedCorrectly = false;

	            while (attempts < maxAttempts && !hasGuessedCorrectly) {
	                System.out.println("Attempt " + (attempts + 1) + ": Enter your guess (1-100):");
	                int userGuess = scanner.nextInt();
	                attempts++;

	                if (userGuess == numberToGuess) {
	                    System.out.println("Congratulations! You guessed the number correctly.");
	                    hasGuessedCorrectly = true;
	                    score += (maxAttempts - attempts + 1); // Add score based on remaining attempts
	                } else if (userGuess < numberToGuess) {
	                    System.out.println("Your guess is too low. Try again.");
	                } else {
	                    System.out.println("Your guess is too high. Try again.");
	                }
	            }

	            if (!hasGuessedCorrectly) {
	                System.out.println("Sorry! You've used all your attempts. The correct number was " + numberToGuess + ".");
	            }

	            System.out.println("Your score: " + score);
	            System.out.println("Do you want to play another round? (yes/no)");
	            String userResponse = scanner.next();
	            playAgain = userResponse.equalsIgnoreCase("yes");
	            round++;
	        }

	        System.out.println("Thank you for playing! Your final score is: " + score);
	        scanner.close();
	    }
	}
