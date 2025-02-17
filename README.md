Q.1: Solution
import java.util.*;
public class ArrayReverser {

    public static void reverse(float[] arr) {
        int start = 0;
        int end = arr.length - 1;

        while (start < end) {
            // Swap elements at start and end indices
            float temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            // Move indices towards the center
            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        float[] myArray = {5.8f, 2.6f, 9.0f, 3.4f, 7.1f};

        System.out.println("Original array:");
        for (float value : myArray) {
            System.out.print(value + " ");
        }
        System.out.println();

        reverse(myArray);

        System.out.println("Reversed array:");
        for (float value : myArray) {
            System.out.print(value + " ");
        }
        System.out.println();
    }
}

Q.2: Solution
import java.util.Scanner;

public class StudentCGPA {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Student ID: ");
        String studentID = scanner.nextLine();

        System.out.print("No. of Courses: ");
        int numCourses = scanner.nextInt();

        int totalCreditsTaken = 0;
        int totalCreditsEarned = 0;
        double totalGradePoints = 0.0;

        for (int i = 1; i <= numCourses; i++) {
            System.out.println("C" + i + ":");
            System.out.print("Credit (Max 3): ");
            int credit = scanner.nextInt();

            System.out.print("CT (Max 30): ");
            int ct = scanner.nextInt();

            System.out.print("AT (Max 10): ");
            int at = scanner.nextInt();

            System.out.print("FE (Max 60): ");
            int fe = scanner.nextInt();

            int totalMarks = ct + at + fe;
            double gradePoint = calculateGradePoint(totalMarks);
            totalGradePoints += gradePoint * credit;
            totalCreditsTaken += credit;
            if (gradePoint > 0) {
                totalCreditsEarned += credit;
            }
        }

        double cgpa = totalGradePoints / totalCreditsTaken;
        String grade = calculateGrade(cgpa);

        System.out.println("\nStudent ID: " + studentID);
        System.out.println("Credit Taken: " + totalCreditsTaken);
        System.out.println("Credit Earned: " + totalCreditsEarned);
        System.out.printf("CGPA: %.1f\n", cgpa);
        System.out.println("Grade: " + grade);

        scanner.close();
    }

    private static double calculateGradePoint(int totalMarks) {
        if (totalMarks >= 90) return 4.0;
        else if (totalMarks >= 85) return 3.7;
        else if (totalMarks >= 80) return 3.3;
        else if (totalMarks >= 75) return 3.0;
        else if (totalMarks >= 70) return 2.7;
        else if (totalMarks >= 65) return 2.3;
        else if (totalMarks >= 60) return 2.0;
        else if (totalMarks >= 55) return 1.7;
        else if (totalMarks >= 50) return 1.0;
        else return 0.0;
    }

    private static String calculateGrade(double cgpa) {
        if (cgpa >= 3.7) return "A";
        else if (cgpa >= 3.3) return "A-";
        else if (cgpa >= 3.0) return "B+";
        else if (cgpa >= 2.7) return "B";
        else if (cgpa >= 2.3) return "B-";
        else if (cgpa >= 2.0) return "C+";
        else if (cgpa >= 1.7) return "C";
        else if (cgpa >= 1.0) return "C-";
        else return "F";
    }
}

Output:
Student ID: IT23046
Credit Taken: 9
Credit Earned: 9
CGPA: 3.5
Grade: A-
