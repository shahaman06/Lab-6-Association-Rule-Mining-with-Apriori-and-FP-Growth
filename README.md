# Lab 6: Association Rule Mining with Apriori and FP-Growth

## Purpose
This lab demonstrates how to mine frequent itemsets and association rules from transactional data using Apriori and FP-Growth algorithms. It includes data cleaning, pruning rare items, one-hot encoding, frequent itemset mining, rule generation, visualizations, and performance comparison.

## Dataset
- **Online Retail Dataset (CSV)**: A transactional dataset with 500,000+ rows of invoices and product purchases.  
- **Direct CSV link**: [https://raw.githubusercontent.com/dbdmg/data-science-lab/master/datasets/online_retail.csv](https://raw.githubusercontent.com/dbdmg/data-science-lab/master/datasets/online_retail.csv)  
- Columns include `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, and `CustomerID`.

## Files in this repository
- `Lab 6.ipynb` - Jupyter Notebook with full code and visualizations
- `apriori_itemsets.csv` - Frequent itemsets discovered by Apriori
- `fpgrowth_itemsets.csv` - Frequent itemsets discovered by FP-Growth
- `apriori_rules.csv` - Association rules derived from Apriori
- `fpgrowth_rules.csv` - Association rules derived from FP-Growth
- `README.md` - This file

## Key Insights
- FP-Growth ran faster than Apriori on this dataset due to its more efficient candidate generation mechanism.
- Many strong rules are those with moderate-to-high confidence and lift > 1.2.
- Frequent single items are often popular products, but actionable insights come from combinations with high lift and confidence.
- Visualizing confidence vs lift helps quickly identify interesting patterns for business decisions, such as product bundling or cross-selling.

## Preprocessing Notes
- Transactions with cancelled invoices were removed.
- Rare items (occurring in fewer than 5 transactions) were pruned to reduce noise.
- Very long transactions with many items were filtered to improve interpretability.
- One-hot encoding was used to prepare the dataset for Apriori and FP-Growth algorithms.

## Parameter Choices
- `min_support`: 0.01 (1% of transactions) for initial itemset mining.
- `min_confidence`: 0.4 for rule generation.
- `lift > 1.2` used to filter stronger associations.

## Challenges and Solutions
- **Memory constraints**: The one-hot matrix can be large. Pruning rare items and using a sparse representation helps.
- **Too many rules**: Filtering by confidence, lift, and itemset length improves interpretability.
- **Noise from popular items**: Lift threshold avoids trivial rules driven by item popularity.

## How to Run
1. Clone this repository.
2. Ensure the CSV dataset is accessible and update the `DATA_PATH` variable in the notebook if needed.
3. Open `Lab 6.ipynb` and run all cells.
4. Review visualizations and exported CSVs for itemsets and rules.

## Notes
- Association rules indicate co-occurrence patterns, not causation.
- Business decisions should be supported by further validation (e.g., A/B testing or pilot promotions).
