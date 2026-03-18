# Trader Behavior & Market Sentiment Analysis
### Junior Data Scientist Assignment — PrimeTrade.ai

---

## Project Overview

This project explores the relationship between **Bitcoin market sentiment** (Fear & Greed Index) and **trader performance** on Hyperliquid — one of the leading decentralized perpetuals exchanges.

The goal: uncover hidden patterns that can drive smarter, sentiment-aware trading strategies.

---

## Datasets Used

| Dataset | Source | Size | Period |
|---|---|---|---|
| Bitcoin Fear & Greed Index | Alternative.me | 2,644 daily records | Feb 2018 – May 2025 |
| Hyperliquid Historical Trader Data | Hyperliquid | 211,224 trade rows, 32 traders | Jan 2024 – May 2025 |

**Key columns:** `Account`, `Coin`, `Execution Price`, `Size USD`, `Side`, `Direction`, `Closed PnL`, `Fee`, `Timestamp IST`, `sentiment`, `sentiment_score`

---

## Project Structure

```
├── analysis.ipynb                        # Main Jupyter Notebook (all 6 phases)
├── fear_greed_index.csv                  # Dataset 1
├── historical_data.csv                   # Dataset 2
├── trader_sentiment_analysis_report.pdf  # Final PDF report
├── phase2_sentiment_performance.png
├── phase3_trader_behavior.png
├── phase4_trader_analysis.png
├── phase5_coin_analysis.png
├── phase6_final_dashboard.png
└── README.md
```

---

## Methodology

### Phase 1 — Data Preparation
- Parsed timestamps, merged both datasets on date
- Filtered to **84,691 closed trades** only (where real PnL is realized)
- Created `outcome` (Win/Loss/Breakeven), `net_pnl` (after fees), `trade_type` (Long/Short)

### Phase 2 — Sentiment vs Performance
- Computed avg PnL, median PnL, win rate, and volume per sentiment class
- Key finding: **Fear days dominate across every metric**

### Phase 3 — Trader Behavior Under Sentiment
- Long/Short ratio shifts per sentiment
- Trade sizing behavior across market conditions
- Win rate breakdown by trade direction and sentiment

### Phase 4 — Per-Trader Deep Dive
- Full scorecard for all 32 traders
- Trader type classification: Elite / Consistent / Average / Losing
- Heatmap of every trader's PnL across sentiment classes
- Contrarian scoring: who profits most on Fear days?

### Phase 5 — Coin-Level Analysis
- 8 top coins analyzed across 5 sentiment classes
- PnL and win rate heatmaps per coin × sentiment
- Identified best coin-sentiment combinations

### Phase 6 — Strategy Backtesting & Dashboard
- 6 rule-based strategies backtested on real data
- Monthly PnL and sentiment trend analysis
- Final insight dashboard with actionable takeaways

---

## Top Findings

### Sentiment vs Performance Summary

| Sentiment | Avg Net PnL | Win Rate | Volume |
|---|---|---|---|
| Extreme Fear | $94.00 | 80.0% | $55M |
| **Fear** | **$124.69** | **88.6%** | **$234M** |
| Neutral | $67.00 | 83.0% | $97M |
| Greed | $67.71 | 76.1% | $128M |
| Extreme Greed | $45.36 | 87.4% | $48M |

### Strategy Backtesting Results

| Strategy | Trades | Total PnL | Avg PnL | Win Rate |
|---|---|---|---|---|
| Trade on Fear Days | 35,839 | $4,181,477 | $116.67 | 86.3% |
| Trade on Greed Days | 33,003 | $1,928,757 | $58.44 | 80.8% |
| Long only on Fear Days | 23,501 | $1,899,986 | $80.85 | 88.5% |
| Short only on Fear Days | 12,338 | $2,281,491 | $184.92 | 82.2% |
| SOL on Greed Days | 1,286 | $486,566 | $378.36 | 72.8% |
| **ETH on Fear Days** | **2,208** | **$940,016** | **$425.73** | **88.8%** |

---

## Key Actionable Insights

1. **Fear = Best Performance** — Fear days produced $124 avg PnL and 88.6% win rate, the highest of all sentiment classes
2. **Shorting on Fear is the power move** — Short trades on Fear days averaged $206 PnL, 2.5x more than Longs
3. **Traders deploy more capital when scared** — Avg trade size on Fear days ($8,858) is 2.5x that on Extreme Greed days ($3,488)
4. **SOL on Greed = $888 avg PnL** — Highest single coin-sentiment combination in the dataset
5. **ETH on Fear = near-perfect** — 99% win rate on Extreme Fear days, $426 avg PnL on all Fear days
6. **MELANIA is a pure Fear play** — 100% win rate on Extreme Fear, collapses to 50% on Extreme Greed
7. **Top trader made $1.59M with 83% Short strategy** — Proving sentiment-aware shorting is highly profitable
8. **Extreme Greed = worst risk-adjusted returns** — Lowest avg PnL ($45), lowest trade volume, highest loss risk

---

## Trader Profiles (32 Traders)

| Type | Count | Characteristic |
|---|---|---|
| Elite | 16 | Win rate ≥ 85%, profitable overall |
| Consistent | 8 | Win rate ≥ 75%, profitable overall |
| Average | 5 | Profitable but inconsistent |
| Losing | 3 | Net negative PnL |

**Best performer:** `0x083384...` — $1,595,427 total PnL, 83% Short trades, thrives on Fear days

---

## Tech Stack

- **Python 3** — pandas, numpy, matplotlib, seaborn
- **Jupyter Notebook** — end-to-end analysis
- **Data:** 211K+ rows, 16 columns, merged across two sources

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/sumit1kr/trader-sentiment-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn

# 3. Place datasets in the project folder
# fear_greed_index.csv
# historical_data.csv

# 4. Run the notebook
analysis.ipynb```

---

## Author

Sumit Kumar
Submitted for: Junior Data Scientist — Trader Behavior Insights
Company: PrimeTrade.ai
Contact: skr.123y68@gmail.com
