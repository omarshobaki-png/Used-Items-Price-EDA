# Used Items Price EDA

This project looks at a dataset of second-hand item listings collected by students in the ENCS5341 Machine Learning course at Birzeit University. Each of the 120 students listed about 15 used items with a title, description, category, age, condition and price. We merged all the submissions into one dataset, cleaned it, and then explored how category, age and condition are linked to price.

## What's in the repo

- `assignment2_analysis.ipynb`: the main notebook with all the steps (merging, cleaning, EDA, insights and limitations)
- `assignment2_report.docx`: the written report for the assignment
- `data/marketplace_raw.csv`: all 1,801 listings after merging, before cleaning
- `data/marketplace_cleaned.csv`: 1,786 listings after cleaning, with all prices converted to ILS (`price_ils`)
- `reports/category_mapping.csv`: how the category names students wrote were mapped to one set of categories

## What the notebook does

1) Data integration: loads each student's CSV (some needed special handling), renames the columns to one standard set, merges them and links each item to its photo.
2) Cleaning: checks missing values, duplicates (including ones written in another language), price and currency formats, category names, age and condition formats, invalid values and outliers. Prices are converted to ILS so they can be compared. Missing values are not filled and outliers are flagged, not deleted.
3) EDA: descriptive statistics, then univariate, bivariate and multivariate analysis. Prices and ages are skewed, so medians and IQR are reported next to the mean, and Spearman correlation is used next to Pearson.
4) Insights: five main findings, for example that category is linked to price much more than condition or age, and that sellers tend to price in round numbers.
5) Limitations and reflection: what the data can't tell us and what could be collected better next time.

## Data and privacy

The original submissions are not included in this repo because they contain student IDs, names and photos. In the shared CSVs, every student ID was replaced with a label (S001 to S120), so the per-student checks still work but nobody can be identified from the data.

Because of that, the merging steps at the start of the notebook won't run from this repo. To work with the data, load the cleaned file directly:

```python
import pandas as pd

df = pd.read_csv("data/marketplace_cleaned.csv")
```

## Tools

Python 3.11 with pandas, numpy and matplotlib, run in Jupyter (VS Code).
