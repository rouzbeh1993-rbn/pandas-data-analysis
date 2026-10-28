# Unemployment Rate Data Cleaning & Analysis (pandas)

A data cleaning and exploration project using Python, pandas and matplotlib. It takes a raw CSV of
the June 2026 unemployment rate by Metropolitan Statistical Area (MSA), fixes common data-quality
problems and produces a clean dataset plus charts.

## Problem

Raw CSV files usually arrive with inconsistent column names, stray spaces, placeholder values such
as `N/A` or `-`, numbers stored as text (`"1,234"`, `"5.2%"`), duplicate rows and missing values.
Before any analysis can be trusted, these issues have to be found, fixed and documented.

## Approach

The notebook `notebook1.ipynb` follows these steps:

1. **Load and inspect** the raw file (shape, data types, first rows)
2. **Standardize** column names (trim spaces, collapse repeated whitespace) and text values
3. **Replace placeholders** (`N/A`, `null`, `-`, empty strings) with real missing values
4. **Convert numeric columns** stored as text (removes `,` and `%`; a column is converted when at least 80% of its values parse as numbers)
5. **Remove exact duplicate rows**
6. **Report missing values** per column. Gaps are not filled with a median or mode, because that would invent unemployment figures. Rows with no numeric data at all are dropped.
7. **Explore** the cleaned data: summary statistics, a distribution chart and the 10 highest / lowest areas
8. **Save** the cleaned dataset to `output/`

## Project structure

```
pandas-data-analysis/
├── notebook1.ipynb      # cleaning and exploration
├── data/                # place the raw CSV here (not included)
└── output/              # created by the notebook: cleaned CSV and charts
```

## How to run

1. Install the requirements:

   ```
   pip install pandas matplotlib jupyter
   ```

2. Put the raw CSV in the `data/` folder with this name:

   ```
   2026 June Unemployment Rate by Metropolitan Statistical Area (Percent).csv
   ```

3. Open `notebook1.ipynb` and run all cells.

If your file has a different layout, change `VALUE_COL` and `LABEL_COL` in the exploration section.

## Outputs

| File | Description |
|---|---|
| `output/unemployment_cleaned.csv` | Cleaned dataset |
| `output/distribution.png` | Histogram of the unemployment rate with the median marked |
| `output/top10.png` | 10 areas with the highest rate |
| `output/bottom10.png` | 10 areas with the lowest rate |

## Tools

Python · pandas · matplotlib
