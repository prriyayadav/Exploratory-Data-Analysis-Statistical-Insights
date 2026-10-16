# E-commerce Exploratory Data Analysis & Statistical Insights
 
An end-to-end exploratory data analysis (EDA) of 5,852 e-commerce orders from 3,200 customers (India, Jan 2024 - Sep 2026). The project combines descriptive statistics, distribution and outlier analysis, correlation and multivariate views, and three formal hypothesis tests to uncover patterns in discounting, customer retention and delivery performance.
 
> **Note:** the dataset is **synthetic**, generated for portfolio practice. It contains no real customer data, and the effect sizes illustrate the method rather than real market behaviour.
 
## Key findings
 
1. **Deep discounts destroy profit.** Average margin falls from about 36% (no discount) to about -10% in the 31-50% discount band, where roughly two in three orders lose money. Electronics already turns loss-making at 21-30%.
2. **Retention is an inverted-U in discount depth.** Repeat-purchase rate is about 28% for customers with almost no discount, about 52% at 5-20%, and falls to about 38-42% for heavy-discount customers.
3. **Delivery over 3 days hurts satisfaction.** Average rating is about 4.3 for 1-3 days and drops to about 3.5 at 6 days (Spearman rho about -0.46).
4. **Electronics drives revenue, not profit.** About 51% of revenue but about 24% of profit, with an average margin of about 8% versus 35-41% for Fashion and Beauty & Health.
5. **Value is concentrated.** The top 20% of customers generate about 70% of profit, and sales are heavily right-skewed (skewness about 3.5), so medians are more representative than means.
## Hypothesis tests (alpha = 0.05)
 
| # | Question | Test | Result |
|---|---|---|---|
| H1 | Is retention related to discount depth? | Chi-square test of independence (+ Mann-Whitney U) | Reject H0 (p < 1e-20) |
| H2 | Does profit margin differ across discount bands? | Kruskal-Wallis (+ Spearman) | Reject H0 (p < 0.001) |
| H3 | Does slower delivery lower ratings? | Spearman correlation | Reject H0 (rho about -0.46) |
 
Non-parametric tests are used because the money variables are strongly skewed.
 
## Repository contents
 
| File | Description |
|---|---|
| `EDA_Statistical_Insights.ipynb` | Main deliverable: executed notebook with charts, tests and markdown commentary |
| `ecommerce_orders_clean.xlsx` | Cleaned dataset (sheets: `Orders`, `Customers`, `Data_Dictionary`) |
 
## Dataset
 
| Sheet | Rows | Description |
|---|---|---|
| `Orders` | 5,852 | One row per order: dates, customer segment, region, category, price, quantity, discount, sales, profit, shipping, rating, returns |
| `Customers` | 3,200 | One row per customer: order counts, totals, average discount, `Repeat_Customer` flag |
| `Data_Dictionary` | - | Column definitions and cleaning notes |
 
Amounts are in INR. Cleaning applied: no missing values, no duplicate order IDs, consistent types and categories, validated dates. Genuine outliers (corporate bulk orders, expensive electronics, deeply discounted loss-making orders) were deliberately kept and analysed rather than removed.
 
## Methods
 
- **Descriptive statistics:** mean, median, standard deviation, quartiles, IQR, skewness, coefficient of variation
- **Distributions:** histograms with mean/median markers, log-scale view of skewed variables
- **Anomaly detection:** box plots and the 1.5 x IQR rule, with investigation of what the outliers are
- **Correlation:** Spearman heatmap (rank-based, robust to skew)
- **Multivariate views:** category x discount-band margin heatmap, region x category profit heatmap, monthly sales trend, customer Pareto curve
- **Inference:** chi-square, Kruskal-Wallis, Mann-Whitney U, Spearman correlation
## How to run
 
```bash
pip install pandas numpy matplotlib seaborn scipy openpyxl jupyter
jupyter notebook EDA_Statistical_Insights.ipynb
```
 
Keep the notebook and `ecommerce_orders_clean.xlsx` in the same folder. Use **Run All** to reproduce every chart and test.
 
## Limitations and next steps
 
- Results show association, not causation; a randomised discount experiment would be needed to establish causal effects.
- Synthetic data, so conclusions should not be generalised to real businesses.
- Possible extensions: logistic-regression retention model on first-order features, RFM customer segmentation, and a dashboard of the key metrics.
## Tech stack
 
Python, pandas, NumPy, Matplotlib, Seaborn, SciPy, Jupyter
 
