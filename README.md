import java.util.Scanner;

    public class VirtualInterview {

        private static final String[] QUESTIONS = {
                "Tell me about yourself.",
                "Why do you want this job?",
                "What are your strengths?",
                "What are your weaknesses?",
                "Describe a challenge you faced and how you overcame it.",
                "Where do you see yourself in 5 years?",
                "Why should we hire you?"
        };

        private static final String[][] KEYWORDS = {
                {"team", "work", "collaborate", "career", "experience"},
                {"company", "growth", "challenge", "interest", "skills"},
                {"hardworking", "dedicated", "skills", "teamwork"},
                {"improve", "learning", "weakness", "challenge"},
                {"problem", "solution", "challenge", "adapt"},
                {"growth", "career", "development", "skills"},
                {"value", "skills", "experience", "dedicated"}
        };

        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            System.out.println("Welcome to the AI-Powered Virtual Interview!");
            System.out.println("Please answer the following questions:");
            System.out.println("--------------------------------------------------");

            int totalQuestions = QUESTIONS.length;
            int positiveFeedbacks = 0;

            for (int i = 0; i < totalQuestions; i++) {
                System.out.println("Q" + (i+1) + ": " + QUESTIONS[i]);
                System.out.print("Your answer: ");
                String answer = scanner.nextLine().toLowerCase();

                int keywordCount = countKeywords(answer, KEYWORDS[i]);
                if (keywordCount >= 1) {
                    System.out.println("AI Feedback: Good job! Your answer includes relevant keywords.");
                    positiveFeedbacks++;
                } else {
                    System.out.println("AI Feedback: Try to include more relevant details in your answer.");
                }
                System.out.println();
            }

            System.out.println("Interview completed. Summary:");
            double scorePercent = ((double) positiveFeedbacks / totalQuestions) * 100;
            System.out.printf("You provided satisfactory answers to %d out of %d questions (%.1f%%).\n", positiveFeedbacks, totalQuestions, scorePercent);

            if (scorePercent > 75) {
                System.out.println("Overall feedback: Excellent! You are well-prepared.");
            } else if (scorePercent > 50) {
                System.out.println("Overall feedback: Good effort. Consider refining some answers.");
            } else {
                System.out.println("Overall feedback: You might want to practice more before your next interview.");
            }

            System.out.println("Thank you for using the AI-Powered Virtual Interview. Good luck!");
            scanner.close();
        }

        private static int countKeywords(String answer, String[] keywords) {
            int count = 0;
            for (String keyword : keywords) {
                if (answer.contains(keyword)) {
                    count++;
                }
            }
            return count;
        }
    }
