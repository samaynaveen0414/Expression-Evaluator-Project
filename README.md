import parser.ExpressionParser;
import stackExceptionPackage.StackUnderflowException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ExpressionParser parser = new ExpressionParser();
        
        System.out.println("Enter a mathematical expression to evaluate (or type 'exit' to quit):");

        while (true) {
            System.out.print("Expression: ");
            String expression = scanner.nextLine();

            if (expression.equalsIgnoreCase("exit")) {
                System.out.println("Program is done Goodbye!");
                break;
            }
            try {
                double result = parser.evaluate(expression);
                System.out.println("Result: " + result);
                System.out.println("Max Operand Stack Depth: " + parser.getMaxOperandStackDepth());
                System.out.println("Max Operator Stack Depth: " + parser.getMaxOperatorStackDepth());
            } catch (StackUnderflowException e) {
                System.err.println("Error: " + e. getMessage());
            } catch (ArithmeticException e) {
                System.err.println("Error: " + e.getMessage());
            } catch (IllegalArgumentException e) {
                System.err.println("Error: Invalid expression - " + e.getMessage());
            } catch (IllegalStateException e) {
                System.err.println("Error: Expression error - " + e.getMessage());
            }
        }
        scanner.close();
    }
}
