package cinema;

import java.util.Scanner;

public class Cinema {

    int rows;
    int seats;
    int frontRow;
    int backRow;
    int ticketsPurchased;
    int currentIncome;
    int totalIncome;
    double occupied;
    String[][] cinema;

    Cinema(int rows, int seats) {
        this.rows = rows;
        this.seats = seats;
        this.frontRow = rows / 2;
        this.backRow = rows - frontRow;
        this.ticketsPurchased = 0;
        this.occupied = 0;
        this.currentIncome = 0;
        //Calculating the total income from the parameter inputted by the user
        if (rows * seats < 60) {
            this.totalIncome = rows * seats * 10;
        } else {
            int frontRowIncome = frontRow * seats * 10;
            int backRowIncome = backRow * seats * 8;
            this.totalIncome = frontRowIncome + backRowIncome;
        }
        this.cinema = new String[rows][seats];
        //Setting the 2D Array
        System.out.println("Cinema:");
        for (int row = 0; row < cinema.length; row++) {
            for (int col = 0; col < cinema[0].length; col++) {
                cinema[row][col] = "S";
            }
        }
    }

    // Prints all the seats in the Cinema
    public void printSeats() {
        System.out.println("Cinema:");
        for (int col = 0; col <= cinema[0].length; col++) {
            if (col == 0) {
                System.out.print("  ");
            } else {
                System.out.printf("%s ", col);
            }
        }

        for (int row = 0; row < cinema.length; row++) {
            if (row == 0) {
                System.out.println("  ");
            }
            System.out.print(row + 1 + " ");
            for (int col = 0; col < cinema[0].length; col++) {
                System.out.printf("%s ", cinema[row][col]);
            }
            System.out.println();
        }
    }

    // Method to buy the tickets
    public void buyTicket() {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("Enter a row number:");
            int selectRow = Integer.parseInt(scanner.nextLine()) ;
            System.out.println("Enter a seat number in that row:") ;
            int selectSeat = Integer.parseInt(scanner.nextLine());
            System.out.println();
            // Exception handling
            if (selectRow > cinema.length || selectRow < 0 ||
                    selectSeat > cinema[0].length || selectSeat < 0) {
                System.out.println("Wrong input!");
            }else if (cinema[selectRow - 1][selectSeat - 1].startsWith("B")) {
                System.out.println("That ticket has already been purchased");
            } else {
                System.out.printf("Ticket price: $%d%n", priceCheck(selectRow));
                currentIncome += priceCheck(selectRow);
                cinema[selectRow - 1][selectSeat - 1] = "B";
                ticketsPurchased++;
                break;
            }
            System.out.println();
        }

    }

    // Reflects a price of a seat by row
    public int priceCheck(int selectedRow) {

        int frontRow = rows / 2;
        int totalSeats = rows * seats;
        int ticketPrice;

        if (totalSeats <= 60 || selectedRow <= frontRow) {
            ticketPrice = 10;
        } else {
            ticketPrice = 8;
        }

        return ticketPrice;
    }

    // Cinema's statistics
    public void stats() {
        occupied = (double) ticketsPurchased / (rows * seats) * 100;

        System.out.printf("Number of purchased tickets: %d\n", ticketsPurchased);
        System.out.printf("Percentage: %.2f%%\n", occupied);
        System.out.printf("Current income: $%d\n", currentIncome);
        System.out.printf("Total income: $%d\n", totalIncome);
    }

    public void start() {
        Scanner scanner = new Scanner(System.in);
        // The main menu loop
        while (true) {
            System.out.println("1. Show the seats\n2. Buy a ticket\n3. Statistics\n0. Exit");
            int input = Integer.parseInt(scanner.nextLine());
            System.out.println();
            if (input == 0) {
                break;
            }
            switch (input) {
                case 1:
                    printSeats();
                    break;
                case 2:
                    buyTicket();
                    break;
                case 3:
                    stats();
                    break;
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        // Write your code here
        Scanner scanner = new Scanner(System.in);
        // Set the rows
        System.out.println("Enter the number of rows:");
        int rows = Integer.parseInt(scanner.nextLine());
        // Set the seats
        System.out.println("Enter the number of seats in each row:");
        int seats = Integer.parseInt(scanner.nextLine());
        System.out.println();
        // Create new Cinema Object with the input values
        Cinema cinema = new Cinema(rows, seats);
        cinema.start();
        System.out.println();

    }
}
