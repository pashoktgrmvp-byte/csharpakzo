# csharpakzo


public class CoffeeMachine
{
    public static string BuyCoffee(
        in string choice_coffee,
        int payment,
        int choice_sugar,
        ref int water,
        ref int coffee,
        ref int sugar,
        ref int milk,
        in string[] coffeename,
        in int[] coffee_price,
        in int[,] coffeeCost,
        ref int cup,
        ref int balance,
        out string check)
    {
        int indexCoffee = Array.IndexOf(coffeename, choice_coffee);

        if (indexCoffee < 0)
        {
            throw new Exception("Такого напитка нет: " + choice_coffee);
        }

        if (payment < coffee_price[indexCoffee])
        {
            throw new Exception("Денег не хватило:");
        }

        if (cup < 1 || water < coffeeCost[indexCoffee, 0])
        {
            throw new Exception("Не хватает воды.");
        }

        if (coffee < 2 || coffee < coffeeCost[indexCoffee, 0])
        {
            throw new Exception("Не хватает кофе.");
        }
        if (milk < 3 || milk < coffeeCost[indexCoffee, 0])
        {
            throw new Exception("Не хватает молока.");
        }

        if (sugar < 4 || sugar < coffeeCost[indexCoffee, 0])
        {
            throw new Exception("Не хватает сахара.");
        }

        balance += payment;

        check = Convert.ToString(payment);

        string result = $"{choice_coffee}, готов";

        if (choice_sugar <= sugar)
        {
            result += $"({choice_sugar}) кусочками сахара";
        }

        check = Convert.ToString(payment - coffee_price[indexCoffee]);
        return result;
    }
}
