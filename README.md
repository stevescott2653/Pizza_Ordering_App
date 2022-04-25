# Pizza_Ordering_App

using System;

namespace PizzaOrder
{
    internal class Program
    {
        /*              


                 There are four methods:

                   1. A method to calculate the subtotal (not taxes or discounts applied)
                   2. A method to apply the discount
                   3. A method to apply the sales tax
                   4. A method to print out the receipt

                  Pizza Prices:

                      small - $8
                      medium - $12
                      large - $14

                  Discounts:

                      Spend over $100 - 20%
                      Spend over $50 - 10%

                  Tax - 7%                  

               */

        private static void Main(string[] args)
        {
            // Greet user and ask for name
            Console.Write("Welcome! can I please have your name? ");
            string name = Console.ReadLine();

            Console.WriteLine($"Hello {name}! How may I assist you today?");

            // Take orders and convert to ints
            Console.Write("Small Pizzas: ");
            int sm = int.Parse(Console.ReadLine());

            Console.Write("Medium Pizzas: ");
            int med = int.Parse(Console.ReadLine());

            Console.Write("Large Pizzas: ");
            int lg = int.Parse(Console.ReadLine());

            // calculate totals
            double subTotal = CalcOrder(sm, med, lg);
            double discountTotal = ApplyDiscount(subTotal);
            double total = ApplyTax(discountTotal);

            // Show receipt
            Console.WriteLine();
            PrintReceipt(name, total, sm, med, lg);
        }

        public static double CalcOrder(int sm, int med, int lg)
        {
            int smTotal = 8 * sm;
            int medTotal = 12 * med;
            int lgTotal = 14 * lg;

            return smTotal + medTotal + lgTotal;
        }

        public static double ApplyTax(double total)
        {
            return total * 1.07;
        }

        public static double ApplyDiscount(double total)
        {
            if (total >= 100)
                total *= 0.8;
            else if (total >= 50)
                total *= 0.9;

            return total;
        }

        public static void PrintReceipt(string name, double total, int sm, int med, int lg)
        {
            Console.WriteLine("Thank you for order!");

            Console.WriteLine();
            Console.WriteLine($"Name : {name}");
            Console.WriteLine();

            if (sm > 0)
                Console.WriteLine($"Small Pizza x{sm}");

            if (med > 0)
                Console.WriteLine($"Medium Pizza x{med}");

            if (lg > 0)
                Console.WriteLine($"Large Pizza x{lg}");

            Console.WriteLine($"Total : ${total}");

            // format currency
            //Console.WriteLine($"Total : {formatTotal}");
        }
    }
}
