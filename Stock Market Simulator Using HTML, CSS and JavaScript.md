# Stock Market Simulator Using HTML, CSS and JavaScript

 A **Stock Market Simulator** is a web application that lets a user practice buying and selling financial assets using **virtual money**.

 For example, the simulator might give a user:

 > **₹1,00,00,000 virtual cash**

 The user can buy stocks, sell them later, view price movements, manage a portfolio, and see virtual profit or loss.

 It does **not** require real money or real brokerage transactions.

 The most important idea is:

```
HTML       → Structure of the simulator
CSS        → Design and appearance
JavaScript → Logic, calculations, interaction and simulation
```

---

 # 1\. What exactly are we building?

 Imagine a website like this:

```
┌───────────────────────────────────────────────────────┐
│              📈 STOCK MARKET SIMULATOR                │
├───────────────────────────────────────────────────────┤
│                                                       │
│  Virtual Cash             Portfolio Value            │
│  ₹72,50,000               ₹1,08,40,000               │
│                                                       │
│  Total Profit             Return                     │
│  +₹8,40,000               +8.40%                     │
│                                                       │
├───────────────────────────────────────────────────────┤
│                   MARKET                             │
│                                                       │
│  Company       Price       Change       Action        │
│  TCS           ₹3,850      +2.4%       [BUY]         │
│  Infosys       ₹1,620      -0.8%       [BUY]         │
│  Reliance      ₹2,450      +1.2%       [BUY]         │
│  HDFC Bank     ₹1,780      -1.1%       [BUY]         │
│                                                       │
├───────────────────────────────────────────────────────┤
│                  MY PORTFOLIO                         │
│                                                       │
│  Stock      Quantity    Avg Price    Current Value   │
│  TCS          20          ₹3,600        ₹77,000       │
│  Infosys      50          ₹1,650        ₹81,000       │
│                                                       │
├───────────────────────────────────────────────────────┤
│                   TRANSACTIONS                        │
│                                                       │
│  Bought 20 TCS @ ₹3,600                               │
│  Sold 10 Infosys @ ₹1,700                             │
│                                                       │
└───────────────────────────────────────────────────────┘
```

 This is essentially a small **financial-game application**.

---

 # 2\. The three technologies

 The simulator can be divided into three layers.

 ## HTML

 HTML creates the elements.

 For example:

```
<h1>Stock Market Simulator</h1>

<div>
    <h2>Virtual Cash</h2>
    <p>₹1,00,00,000</p>
</div>

<button>Buy</button>
<button>Sell</button>
```

 HTML answers:

 > **What exists on the page?**

---

 # 3\. CSS

 CSS controls how everything looks.

 For example:

```
body {
    background-color: #f5f7fb;
    font-family: Arial;
}

button {
    background-color: green;
    color: white;
    padding: 10px 20px;
}
```

 CSS answers:

 > **How should the simulator look?**

 It controls:

 - Colors
- Fonts
- Buttons
- Tables
- Cards
- Spacing
- Layout
- Charts
- Responsive design
- Animations

---

 # 4\. JavaScript

 JavaScript is the most important part for the simulator.

 It controls what happens when the user interacts with the application.

 For example:

```
let cash = 10000000;

function buyStock(price, quantity) {
    let cost = price * quantity;

    if (cash >= cost) {
        cash -= cost;
    }
}
```

 JavaScript answers:

 > **What should happen when the user does something?**

 It handles:

 - Buying
- Selling
- Calculating profit/loss
- Updating cash
- Updating portfolio
- Updating prices
- Recording transactions
- Generating simulated price movements
- Updating charts
- Saving data

---

 # 5\. The basic architecture

 A simple simulator can be thought of like this:

```
                 STOCK MARKET SIMULATOR
                          │
           ┌──────────────┼──────────────┐
           │              │              │
           ↓              ↓              ↓
         HTML            CSS        JavaScript
           │              │              │
       Structure         Design         Logic
                                          │
                    ┌─────────────────────┼─────────────────────┐
                    │                     │                     │
                    ↓                     ↓                     ↓
                 Market                Trading              Portfolio
                 Prices                 BUY/SELL              Tracking
                    │                     │                     │
                    └─────────────────────┼─────────────────────┘
                                          ↓
                                  User's Dashboard
```

---

 # 6\. The main components

 A good stock simulator usually has several sections.

 ## 6.1 Dashboard

 The dashboard gives the user a quick summary.

 For example:

```
Virtual Cash       ₹72,00,000

Portfolio Value    ₹1,08,00,000

Total Investment   ₹1,00,00,000

Profit/Loss        +₹8,00,000

Return             +8%
```

 These values are calculated by JavaScript.

---

 # 7\. Starting virtual money

 When the game begins:

```
let initialCapital = 10000000;
let cash = initialCapital;
```

 Here:

```
₹10,000,000
```

 is ₹1 crore.

 You could also choose:

```
let initialCapital = 1000000;
```

 for ₹10 lakh.

 Or:

```
let initialCapital = 100000;
```

 for ₹1 lakh.

 The important thing is that this is **virtual money**.

---

 # 8\. Representing stocks in JavaScript

 You need some way to store information about each stock.

 One simple approach is an array of objects:

```
const stocks = [
    {
        symbol: "TCS",
        name: "Tata Consultancy Services",
        price: 3850
    },
    {
        symbol: "INFY",
        name: "Infosys",
        price: 1620
    },
    {
        symbol: "RELIANCE",
        name: "Reliance Industries",
        price: 2450
    }
];
```

 Now JavaScript knows:

```
TCS       → ₹3,850
INFY      → ₹1,620
RELIANCE  → ₹2,450
```

---

 # 9\. Representing the user's portfolio

 The portfolio needs different information.

 For example:

```
const portfolio = {
    TCS: {
        quantity: 20,
        averagePrice: 3600
    },

    INFY: {
        quantity: 50,
        averagePrice: 1650
    }
};
```

 This means:

```
TCS
20 shares
Average purchase price = ₹3,600

INFY
50 shares
Average purchase price = ₹1,650
```

---

 # 10\. Buying a stock

 Suppose:

```
TCS price = ₹3,850
```

 The user wants:

```
Quantity = 10
```

 The cost is:

```
Price × Quantity

₹3,850 × 10

= ₹38,500
```

 JavaScript can calculate this:

```
const cost = stock.price * quantity;
```

 Then we check whether the user has enough cash:

```
if (cash >= cost) {
    cash -= cost;
}
```

 If the user has ₹1 crore:

```
Before buying:

Cash = ₹1,00,00,000

Buy TCS:

10 × ₹3,850
= ₹38,500

After buying:

Cash = ₹99,61,500
```

 The portfolio now contains:

```
TCS
Quantity: 10
Average Price: ₹3,850
```

---

 # 11\. What happens when the user clicks BUY?

 The complete flow is:

```
User clicks BUY
       ↓
Select stock
       ↓
Enter quantity
       ↓
Get current price
       ↓
Calculate cost
       ↓
Check available cash
       ↓
Is cash sufficient?
      / \
    YES  NO
     ↓    ↓
Complete  Show error
purchase
     ↓
Deduct cash
     ↓
Add shares
     ↓
Update portfolio
     ↓
Record transaction
     ↓
Refresh dashboard
```

 This is one of the most important workflows in the application.

---

 # 12\. Selling a stock

 Selling works in the opposite direction.

 Suppose:

```
TCS current price = ₹4,000

User owns = 10 shares
```

 The user sells 5 shares.

 Value:

```
5 × ₹4,000
= ₹20,000
```

 Cash increases:

```
Before sale = ₹99,61,500

Sale proceeds = ₹20,000

After sale = ₹99,81,500
```

 Portfolio quantity becomes:

```
10 - 5 = 5 shares
```

---

 # 13\. Preventing invalid sales

 The simulator must check whether the user actually owns enough shares.

 For example:

```
if (portfolio.TCS.quantity >= quantity) {
    // allow sale
} else {
    // reject sale
}
```

 If the user owns 10 shares and tries to sell 20:

```
❌ You don't own enough shares.
```

 This is part of **input validation**.

---

 # 14\. Calculating portfolio value

 Suppose the user owns:

```
TCS:
20 shares
Current price = ₹3,850

INFY:
50 shares
Current price = ₹1,620
```

 Portfolio value:

```
TCS

20 × ₹3,850
= ₹77,000

INFY

50 × ₹1,620
= ₹81,000
```

 Total:

```
₹77,000 + ₹81,000

= ₹1,58,000
```

 JavaScript can calculate this dynamically.

---

 # 15\. Total account value

 A user's total account value can be thought of as:

```
Cash + Current Portfolio Value
```

 For example:

```
Cash                 ₹98,42,000
Stock value           ₹1,58,000
                     ───────────
Total account value  ₹1,00,00,000
```

 If stock prices subsequently rise:

```
Cash                 ₹98,42,000
Stock value           ₹1,70,000
                     ───────────
Total account value  ₹1,00,12,000
```

 The user now has a virtual gain of:

```
₹12,000
```

---

 # 16\. Calculating profit and loss

 A basic calculation is:

```
Profit/Loss =
Current Total Value - Initial Capital
```

 For example:

```
Initial capital = ₹1,00,00,000

Current value = ₹1,08,00,000

Profit = ₹8,00,000
```

 If the current value falls:

```
Initial capital = ₹1,00,00,000

Current value = ₹96,00,000

Loss = -₹4,00,000
```

---

 # 17\. Calculating percentage return

 You can calculate:

```
Return % =
(Profit / Initial Capital) × 100
```

 Example:

```
Profit = ₹8,00,000
Initial capital = ₹1,00,00,000
```

 Therefore:

```
(8,00,000 / 1,00,00,000) × 100
= 8%
```

 The dashboard could show:

```
Profit: ₹8,00,000

Return: +8.00%
```

---

 # 18\. The most interesting part: simulated prices

 A simulator needs prices to change.

 There are two fundamentally different approaches.

 ## Approach A — Use real market data

 Your JavaScript application gets market prices from an external service/API.

 Conceptually:

```
Your website
     ↓
API request
     ↓
Market data service
     ↓
Current/available market data
     ↓
JavaScript
     ↓
Update UI
```

 This makes the simulator more closely connected to actual market conditions.

 However, this requires:

 - An appropriate data provider
- API access
- Handling rate limits
- Handling errors
- Potential authentication
- Data licensing considerations
- A backend in some architectures

---

 # 19\. Approach B — Generate simulated prices

 For a purely educational game, you can generate artificial price movements.

 For example:

```
function updatePrice(price) {
    const change = (Math.random() - 0.5) * 0.04;

    return price * (1 + change);
}
```

 Conceptually:

```
Current price
     ↓
Generate random movement
     ↓
Calculate new price
     ↓
Update market
     ↓
Update portfolio
```

 This does **not** represent a prediction of what a real stock will do.

 It's simply a game mechanic.

---

 # 20\. Example of simulated movement

 Suppose:

```
TCS = ₹3,850
```

 The simulator generates:

```
+1.2%
```

 New price:

```
₹3,850 × 1.012
≈ ₹3,896.20
```

 Later it might generate:

```
-0.8%
```

 and the price decreases.

 You could update prices every few seconds:

```
setInterval(updateMarket, 5000);
```

 This means the simulator can update the market approximately every 5 seconds.

---

 # 21\. Why randomness isn't enough for a realistic simulator

 A beginner might think:

```
price = random number
```

 But that produces poor simulations.

 A better educational simulator might incorporate:

 - Previous price
- Volatility
- Trends
- Random shocks
- Market-wide events
- Sector movements
- Different volatility for different assets

 For example:

```
Market
  ↓
 ┌──────────────┐
 │ Overall trend│
 └──────┬───────┘
        ↓
 ┌──────────────┐
 │ Sector trend │
 └──────┬───────┘
        ↓
 ┌──────────────┐
 │ Stock effect │
 └──────┬───────┘
        ↓
 ┌──────────────┐
 │ Random noise │
 └──────┬───────┘
        ↓
   New price
```

 That can create a more interesting game.

---

 # 22\. Stock price chart

 A good simulator should show historical simulated prices.

 For example:

```
Price
₹4000 │             ╭──╮
      │        ╭────╯  ╰─╮
₹3800 │    ╭───╯          ╰──
      │ ╭──╯
₹3600 │─╯
      └────────────────────────
        1   2   3   4   5   6
                 Time
```

 The chart helps users visually understand:

 - Price increases
- Price decreases
- Volatility
- Trends
- High/low points

 You can implement simple charts yourself with HTML/CSS/JavaScript or use a charting library.

---

 # 23\. Transaction history

 Every trade should be recorded.

 For example:

```
const transactions = [
    {
        type: "BUY",
        symbol: "TCS",
        quantity: 10,
        price: 3850
    },
    {
        type: "SELL",
        symbol: "INFY",
        quantity: 5,
        price: 1700
    }
];
```

 The UI can display:

 | Type | Stock | Quantity | Price | Value |
| --- | --- | --- | --- | --- |
| BUY | TCS | 10 | ₹3,850 | ₹38,500 |
| SELL | INFY | 5 | ₹1,700 | ₹8,500 |

This creates an audit trail of what the user did.

---

 # 24\. Portfolio table

 The portfolio might display:

 | Stock | Quantity | Avg. Buy Price | Current Price | Current Value | P/L |
| --- | --- | --- | --- | --- | --- |
| TCS | 20 | ₹3,600 | ₹3,850 | ₹77,000 | +₹5,000 |
| INFY | 50 | ₹1,650 | ₹1,620 | ₹81,000 | -₹1,500 |

JavaScript calculates these values whenever the market changes.

---

 # 25\. Average purchase price

 Suppose you initially buy:

```
10 TCS @ ₹3,500
```

 Then later:

```
10 TCS @ ₹3,900
```

 Total amount invested:

```
10 × ₹3,500 = ₹35,000

10 × ₹3,900 = ₹39,000

Total = ₹74,000
```

 Total quantity:

```
20 shares
```

 Average price:

```
₹74,000 / 20

= ₹3,700
```

 So:

```
Quantity = 20
Average price = ₹3,700
```

 This is an important piece of portfolio logic.

---

 # 26\. Unrealized vs realized profit

 A more advanced simulator should distinguish these.

 ### Unrealized profit

 You still own the stock.

 Example:

```
Bought at ₹3,500
Current price = ₹3,900
```

 You have a paper/unrealized gain of:

```
₹400 per share
```

 But you haven't sold it.

 ### Realized profit

 You actually sell the stock.

```
Bought = ₹3,500
Sold = ₹3,900

Realized gain = ₹400 per share
```

 A simulator can display both separately.

---

 # 27\. Buy/Sell modal

 Instead of immediately buying when the user clicks a button, you could open a small dialog:

```
┌──────────────────────────────┐
│         BUY TCS              │
├──────────────────────────────┤
│ Current Price: ₹3,850        │
│                              │
│ Quantity: [  10  ]           │
│                              │
│ Estimated Cost: ₹38,500      │
│                              │
│       [ Cancel ] [ BUY ]     │
└──────────────────────────────┘
```

 JavaScript reads the quantity and performs the transaction.

---

 # 28\. Search and filtering

 If the simulator has many assets:

```
Search: [ TCS                 ]

☑ Stocks
☐ Bonds
☐ Mutual Funds
☐ Crypto
```

 JavaScript can filter the list.

 For example:

```
User enters "TCS"
       ↓
JavaScript searches stock list
       ↓
Only matching stocks displayed
```

 This makes the application more usable.

---

 # 29\. Portfolio allocation

 You could also show how the user's money is distributed.

 For example:

```
Portfolio Allocation

Stocks       ███████████████████ 60%
Bonds        ██████              20%
Mutual Funds █████               15%
Cash         ██                   5%
```

 This can help students understand **diversification and asset allocation**.

---

 # 30\. Risk levels

 For an educational simulator, you can assign fictional or educational risk categories.

 For example:

```
Stock A → Low
Stock B → Medium
Stock C → High
```

 But be careful: a simulator's label should not be presented as a real-world investment recommendation.

 The application is primarily for learning.

---

 # 31\. Challenges and scoring

 You can turn the simulator into a game.

 For example:

```
Challenge:
Start with ₹1 crore.

Goal:
Build and manage a portfolio for 30 simulated days.

Rules:
- Maximum 30% in one stock
- Minimum ₹10 lakh cash
- Trading allowed every simulated day
```

 Then the application tracks the user's actions.

 You could award points for completing educational objectives rather than simply rewarding returns.

 For example:

```
Diversification completed       +100 points
Completed 10 trades              +50 points
Reviewed transaction history     +25 points
Completed risk quiz              +100 points
```

 This makes the simulator more educational.

---

 # 32\. HTML structure

 A simplified HTML structure could look like:

```
<!DOCTYPE html>
<html>
<head>
    <title>Stock Market Simulator</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <header>
        <h1>📈 Stock Market Simulator</h1>
    </header>

    <main>

        <section id="dashboard">
            <div class="card">
                <h3>Virtual Cash</h3>
                <p id="cash">₹1,00,00,000</p>
            </div>

            <div class="card">
                <h3>Portfolio Value</h3>
                <p id="portfolio-value">₹0</p>
            </div>

            <div class="card">
                <h3>Profit/Loss</h3>
                <p id="profit-loss">₹0</p>
            </div>
        </section>

        <section id="market">
            <h2>Market</h2>
            <div id="stock-list"></div>
        </section>

        <section id="portfolio">
            <h2>My Portfolio</h2>
            <div id="portfolio-list"></div>
        </section>

        <section id="transactions">
            <h2>Transactions</h2>
            <div id="transaction-list"></div>
        </section>

    </main>

    <script src="script.js"></script>

</body>
</html>
```

 Notice something important:

 HTML doesn't need to contain every stock.

 JavaScript can generate the stock rows dynamically.

---

 # 33\. CSS structure

 You could create cards:

```
#dashboard {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.card {
    background: white;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
```

 Then style the buttons:

```
.buy-button {
    background: #16a34a;
    color: white;
    border: none;
    padding: 8px 15px;
    border-radius: 6px;
}

.sell-button {
    background: #dc2626;
    color: white;
    border: none;
    padding: 8px 15px;
    border-radius: 6px;
}
```

---

 # 34\. JavaScript architecture

 Instead of putting everything into one huge JavaScript function, divide the application into logical pieces.

 For example:

```
script.js

├── Market Data
│   ├── stocks
│   └── prices
│
├── User Account
│   ├── cash
│   └── initial capital
│
├── Portfolio
│   ├── holdings
│   └── calculations
│
├── Trading
│   ├── buyStock()
│   └── sellStock()
│
├── Market Simulation
│   └── updatePrices()
│
├── Transactions
│   └── recordTransaction()
│
└── UI
    ├── renderMarket()
    ├── renderPortfolio()
    └── updateDashboard()
```

 This is much easier to maintain.

---

 # 35\. A simple data model

 You can think of the application data like this:

```
const game = {
    initialCapital: 10000000,

    cash: 10000000,

    stocks: {},

    portfolio: {},

    transactions: [],

    priceHistory: {}
};
```

 This is essentially the **state of the game**.

 As the user interacts with the application, this state changes.

---

 # 36\. What does "state" mean?

 State simply means:

 > **The information describing what the application currently looks like and what has happened so far.**

 For example:

```
cash = ₹75 lakh

TCS = 20 shares

INFY = 50 shares

TCS current price = ₹3,900

Last transaction = BUY TCS
```

 That is the current state of the simulator.

 JavaScript manages this state.

---

 # 37\. Rendering

 After JavaScript changes the state, the screen needs to reflect the new values.

 For example:

```
Before BUY:

Cash = ₹1,00,00,000
TCS = 0 shares
```

 User buys 10 TCS.

 JavaScript changes the state:

```
Cash = ₹99,61,500
TCS = 10 shares
```

 Then the UI is updated:

```
Dashboard
   ↓
Cash changes

Portfolio
   ↓
TCS appears

Transactions
   ↓
BUY TCS appears
```

 This process is often called **rendering/updating the UI**.

---

 # 38\. LocalStorage

 If you only keep everything in JavaScript variables, refreshing the browser can reset the game.

 You can use the browser's `localStorage` for a simple version.

 For example:

```
localStorage.setItem(
    "portfolio",
    JSON.stringify(portfolio)
);
```

 Later:

```
const savedPortfolio =
    JSON.parse(localStorage.getItem("portfolio"));
```

 This lets the simulator remember information between page refreshes.

 For a more advanced application, you would generally use a backend/database instead of relying only on localStorage.

---

 # 39\. Backend: when do you need one?

 A basic project can work entirely in the browser:

```
HTML
CSS
JavaScript
      ↓
Browser
```

 But a larger application might use:

```
Frontend
HTML + CSS + JavaScript
        ↓
      API
        ↓
     Backend
        ↓
    Database
```

 The backend could store:

 - User accounts
- Portfolios
- Transactions
- Leaderboards
- Game sessions
- Historical data
- Competition results

---

 # 40\. Example full architecture

 For a larger educational platform:

```
                    USER
                     │
                     ↓
             ┌───────────────┐
             │   Frontend    │
             │ HTML/CSS/JS   │
             └───────┬───────┘
                     │
                     ↓
                REST API
                     │
             ┌───────┴────────┐
             ↓                ↓
        Application        Market Data
          Backend             Service
             │
             ↓
          Database
             │
             ├── Users
             ├── Portfolios
             ├── Trades
             └── History
```

 The browser handles the interface, while the backend handles persistent application data and business rules.

---

 # 41\. Important distinction: simulator vs real trading application

 This is extremely important.

 A **stock-market simulator**:

```
Virtual money
      ↓
Simulated or educational market data
      ↓
Virtual trades
      ↓
Virtual profit/loss
```

 A **real trading application**:

```
Real money
      ↓
Brokerage infrastructure
      ↓
Actual orders
      ↓
Real securities
      ↓
Real financial consequences
```

 A beginner's HTML/CSS/JavaScript project should normally stay in the first category.

---

 # 42\. Suggested project structure

 A clean beginner project might look like:

```
stock-market-simulator/
│
├── index.html
│
├── css/
│   └── style.css
│
├── js/
│   ├── app.js
│   ├── market.js
│   ├── portfolio.js
│   ├── trading.js
│   └── ui.js
│
├── data/
│   └── stocks.js
│
└── assets/
    └── images/
```

 For a small project, however, you can start with:

```
stock-market-simulator/
│
├── index.html
├── style.css
└── script.js
```

 Then split the code into modules as the project grows.

---

 # 43\. Development stages

 Don't try to build everything at once.

 A good progression is:

 ### Level 1 — Static interface

 Build:

 - Header
- Dashboard
- Market table
- Portfolio table
- Buttons

 No actual functionality yet.

```
HTML + CSS
```

---

 ### Level 2 — Virtual money

 Add:

```
let cash = 10000000;
```

 Display it on the dashboard.

---

 ### Level 3 — Stock data

 Create:

```
const stocks = [...]
```

 Display stocks dynamically.

---

 ### Level 4 — BUY functionality

 Implement:

```
Select stock
→ Enter quantity
→ Calculate cost
→ Check cash
→ Deduct cash
→ Add shares
```

---

 ### Level 5 — SELL functionality

 Implement:

```
Select stock
→ Enter quantity
→ Check holdings
→ Calculate sale
→ Increase cash
→ Reduce shares
```

---

 ### Level 6 — Portfolio calculations

 Add:

 - Portfolio value
- Average price
- Profit/loss
- Return percentage

---

 ### Level 7 — Price simulation

 Add changing prices.

```
Price
  ↓
Simulation
  ↓
New price
  ↓
Portfolio recalculation
```

---

 ### Level 8 — Charts

 Add price-history charts.

---

 ### Level 9 — Transaction history

 Record every trade.

---

 ### Level 10 — Persistence

 Use localStorage or a backend/database.

---

 ### Level 11 — Advanced features

 Add:

 - Multiple asset classes
- Challenges
- Leaderboards
- User accounts
- Achievements
- Portfolio analytics
- News/event simulation
- Multiple game modes

---

 # 44\. A complete user journey

 Imagine a student opens the simulator.

 ### Step 1

 The application gives:

```
₹1,00,00,000 virtual cash
```

 ### Step 2

 They see:

```
TCS       ₹3,850
INFY      ₹1,620
RELIANCE  ₹2,450
```

 ### Step 3

 They choose TCS.

```
Quantity: 20
```

 ### Step 4

 JavaScript calculates:

```
20 × ₹3,850
= ₹77,000
```

 ### Step 5

 The system checks:

```
Cash ≥ ₹77,000?
```

 Yes.

 ### Step 6

 The simulator executes the virtual trade.

```
Cash:
₹1,00,00,000
        ↓
₹99,23,000
```

 Portfolio:

```
TCS
20 shares
Average price = ₹3,850
```

 ### Step 7

 The simulated market changes.

```
TCS
₹3,850 → ₹4,000
```

 ### Step 8

 Portfolio value becomes:

```
20 × ₹4,000
= ₹80,000
```

 ### Step 9

 Unrealized gain:

```
₹80,000 - ₹77,000
= ₹3,000
```

 The dashboard updates automatically.

---

 # 45\. What you learn by building this project

 This project is useful because it teaches much more than HTML/CSS.

 ### HTML skills

 You learn:

 - Semantic structure
- Forms
- Tables
- Buttons
- Inputs
- Modals
- Sections

 ### CSS skills

 You learn:

 - Flexbox
- Grid
- Responsive design
- Cards
- Tables
- Colors
- Animations
- Mobile layouts

 ### JavaScript skills

 You learn:

 - Variables
- Objects
- Arrays
- Functions
- Events
- DOM manipulation
- Conditional statements
- Loops
- Mathematical calculations
- Timers
- LocalStorage
- State management

 ### Software-development skills

 You also learn:

 - Data modeling
- Validation
- Debugging
- UI design
- Application architecture
- Separating logic from presentation
- Managing application state

---

 # 46\. The key concept to understand

 The entire simulator can ultimately be reduced to this loop:

```
              ┌──────────────────┐
              │   Current State   │
              │                  │
              │ Cash             │
              │ Portfolio        │
              │ Stock Prices     │
              │ Transactions     │
              └────────┬─────────┘
                       │
                       ↓
                User interaction
                       │
              ┌────────┴─────────┐
              ↓                  ↓
            BUY/SELL        Market movement
              │                  │
              └────────┬─────────┘
                       ↓
                 Update state
                       ↓
                 Recalculate
                       ↓
                  Render UI
                       │
                       ↓
                User sees result
                       │
                       └──────────→ repeat
```

 That's the heart of a simulator.

 ## In very simple terms

 **HTML** builds the stock-market simulator's body:

 > "Here is the portfolio, here are the stocks, here are the buttons."

 **CSS** makes it look like an application:

 > "Make the dashboard attractive, organize the tables, color profits green and losses red."

 **JavaScript** makes it actually work:

 > "The user bought 20 shares. Deduct the money, add the shares, calculate the portfolio value, record the trade, and update the screen."

 And the **simulation engine** creates the changing environment:

 > "The market has moved, so update the prices and recalculate the user's portfolio."

 So the project is essentially:

 **HTML + CSS + JavaScript \+ financial/game logic = Stock Market Simulator.**
