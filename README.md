
<p align="center">
  <a href="#">
    <img src="./public/demo.png" width="650rem" alt="Demonstração do Smart Spending Checker">
  </a>
</p>

# Smart Spending Checker

Version: CLI

Smart Spending Checker is a simple system to help you control your monthly spending, allowing you to add installment purchases and track their impact on your budget.

> **Note:** The program runs in Brazilian Portuguese (`pt-BR`). All menus, prompts, and messages will be displayed in Portuguese.

## Features

*   **Add product:** Register a new product with installments, specifying the name, total value, and number of installments.
*   **Remove product:** Delete a product from your spending list.
*   **List months:** View products registered for each month.
*   **Update monthly profit:** Set or change your monthly profit to calculate the percentage used by your expenses.
*   **Edit product:** Modify information for an existing product, such as name, total value, and number of installments.
*   **Anticipate installments:** Calculate the total amount to pay if you want to anticipate a specific number of installments for a product.
*   **Monthly summary:** See a summary for the month, including your monthly profit, total installments, percentage used, and a strategy recommendation.

## Important Note on Strategy

The program provides a recommendation based on the percentage of your monthly profit used for installments. It's generally recommended to keep your spending below 70% of your monthly profit. If the percentage exceeds this threshold, the program will advise against using your profit to pay for it and suggest creating a separate fund.

### Notes

- The program saves data in the data/products.json file, so make sure the data folder and products.json file exist and have the correct permissions.
- The program accepts both comma (,) and dot (.) as decimal separators when entering values.


## How to Use

### Prerequisites

*   [Go](https://golang.org/dl/) installed and configured on your system.

### Installation

1.  Clone the repository:

    ```bash
    git clone https://github.com/pedrorcruzz/smart-spending-checker.git
    cd smart-spending-checker
    ```

2.  Run the program:

    ```bash
    go run main.go
    ```

3. **Or build the executable:**

    ```bash
    go build -o gestor-renda  # Replace "gestor-renda" with your preferred app name
    ```

    This will generate a binary named `gestor-renda` in the current folder.

### Setup

1.  **Create the `data` folder:**

    ```bash
    mkdir data
    ```

2.  **Create the `products.json` file inside the `data` folder:**

    The `products.json` file is where the program stores your products and monthly profit data. If the file does not exist, the program will automatically create it with default values.

    Example content for `products.json`:

    ```json
    {
      "products": [],
      "monthly_profit": 0,
      "month": 5,
      "year": 2025
    }
    ```

    You can create the file manually or let the program create it on first run.

### Usage

1.  Run the program:

    ```bash
    go run main.go
    ```

1.2 Run the Program After Building

      ./gestor-renda  # Replace "gestor-renda" with your app name
       
2.  Follow the menu instructions to add, remove, list, or edit products, update your monthly profit, and anticipate installments.

## Automating Access from Anywhere in the Terminal

To run the Smart Spending Checker from any directory in your terminal, you can create a shell script and a function (or alias).

### 1. Create a Shell Script

Create a file named `smart-spending-checker.sh` (or any name you prefer) in a directory of your choice (e.g., `~/.dotfiles/scripts`). Add the following content to the script, **replacing the `cd` path with the actual path to your `smart-spending-checker` directory**:

```bash
#!/bin/bash

cd ~/Developer/Scripts/smart-spending-checker  # ⚠️ REPLACE THIS WITH YOUR ACTUAL PATH

./gestor-renda  # ⚠️ REPLACE THIS WITH YOUR APP NAME
sleep 1.3
clear
```

### 2. Make the Script Executable

Give the script execute permissions:

```bash
chmod +x smart-spending-checker.sh
```

### 3. Create a Function (Fish Shell) or Alias (Zsh/Bash)

#### Fish Shell

Add the following function to your ~/.config/fish/config.fish file:

```fish
function gestor-renda
    set prev_dir (pwd)
    cd ~/.dotfiles/scripts # ⚠️ REPLACE THIS WITH THE DIRECTORY CONTAINING YOUR SCRIPT
    ./smart-spending-checker.sh
    cd $prev_dir
end
```

#### Zsh/Bash

Add the following alias to your ~/.zshrc or ~/.bashrc file:

```bash
alias gestor-renda="cd ~/.dotfiles/scripts && ./smart-spending-checker.sh && cd -" # ⚠️ REPLACE THIS WITH THE DIRECTORY CONTAINING YOUR SCRIPT

```

### 4. Reload Your Shell Configuration

After adding the function or alias, reload your shell configuration:

#### Fish

```bash
source ~/.config/fish/config.fish
```

#### Zsh

```bash
source ~/.zshrc
```

#### Bash

```bash
source ~/.bashrc
```

Now you can run the Smart Spending Checker from any directory by typing gestor-renda in your terminal.




## Contributing

Contributions are welcome! Feel free to open issues and submit pull requests.

## License

This project is licensed under the [MIT License](LICENSE).
