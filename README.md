# 🧮 AssemblyCalculator

Calculator programmed in Assembly Architecture
**Computer Organization and Programming Course**
*Shankar College of Design & Engineering*

---

## 🔧 Major Design & Implementation Decisions

* A custom `atoi` function converts strings to integers, handling input validation and error detection.
* The function checks if the operator is valid (`+`, `-`, `*`, `/`) and rejects multiple or misplaced operators.
* It supports signed numbers by counting minus signs (even = positive, odd = negative).
* Input is limited to the valid 16-bit signed integer range: `-32,768` to `+32,767`.

---

## 🧠 High-Level Algorithm (C-like Pseudocode)

```c
int main() {
    char Operator;
    int result = 0;
    int NUM1 = 0, NUM2 = 0;

    print_string("End Input: (Enter) | Exit: (X or x) | Op: (+, -, *, /)\n");

    while (1) {
        print_string(" -> ");
        scanf("%d", &NUM1);
        NUM1 = ATOI(NUM1);

        scanf("%c", &Operator);
        Operator = ATOI(Operator);

        scanf("%d", &NUM2);
        NUM2 = ATOI(NUM2);

        switch (Operator) {
            case '+':
                result = ADD_FUNC(NUM1, NUM2);
                break;
            case '-':
                result = SUBTRACT_FUNC(NUM1, NUM2);
                break;
            case '*':
                result = multiply(&abs(NUM1), &abs(NUM2));
                if (NUM1 < 0 ^ NUM2 < 0) result = -result;
                break;
            case '/':
                if (NUM2 == 0) print_string("Err: division by 0\n");
                result = divide(&abs(NUM1), &abs(NUM2));
                if (NUM1 < 0 ^ NUM2 < 0) result = -result;
                print_string("Rem : ");
                print_num(abs(NUM1 % NUM2));
                break;
            default:
                print_string("Err: invalid Input \n");
                break;
        }

        print_num(result);
    }
}
```

---

## ▶️ How to Run

1. Open **Mano CPU Simulator**.
2. Load the calculator code:

   * Click **Load**
   * Paste code from the `.txt` file
   * Click **Assemble/Load**
3. Open **KB/Screen CH0**
4. Click **Run**

---

## 💡 Usage Instructions

* **Prompt:**

  ```
  End Input: (Enter) | Exit: (X or x) | Operators: (+, -, *, /)
  ```

* **Input format:**
  Enter a full expression like: `--13 + 7`

  * Even number of minus signs → positive
  * Odd number of minus signs → negative

* **Errors include:**

  * Invalid character or format
  * Repeated or misplaced operator
  * Out-of-range number (< -32,768 or > 32,767)
  * Division by zero

* **Exit:** Type `X` or `x` anytime

---

## 🧪 Extra Features

### ✔️ Sophisticated Input (15%)

* One-line input: supports chained minus signs before numbers
* `atoi` handles sign detection and validation

### ⚡ Fast Multiplication (5%)

* Bitwise multiplication algorithm
* Simulates binary multiplication via shifting and adding

### 🚫 Overflow/Underflow Checks (5%)

* `atoi` verifies value range before conversion
* `CHECK_MSB` detects arithmetic overflow/underflow in addition using MSBs
