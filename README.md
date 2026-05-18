# Etsy Retail Marketing Analysis

This repository contains a complete data analysis project that studies how product-description signals on Etsy relate to listing popularity. The project uses text processing, sentiment analysis, emotion scoring, feature engineering, exploratory visualization, and OLS regression modeling to evaluate whether cause-marketing language, handmade language, sentiment, and other linguistic features are associated with customer demand.

The main project notebook is:

```text
analysis.ipynb
```

## Project Objective

The goal of this project is to understand which product-description and listing-level factors predict Etsy listing popularity, measured using the log-transformed review count:

```text
LogReviewCount = log(reviews_count + 1)
```

The analysis focuses on the following research questions:

1. Do listings that mention social impact, donations, charities, or cause-related language receive more customer engagement?
2. Does handmade positioning affect listing popularity?
3. How does sentiment in product descriptions relate to review count?
4. Do linguistic features such as lexical diversity, personalization language, readability, and trust-building language improve prediction?
5. Which variables remain significant after controlling for price, rating, and product category?

## Dataset

The project uses an Etsy listing dataset stored as:

```text
data/etsy.csv
```

The original dataset contains **10,406 listings** with fields such as:

- `url`
- `name`
- `price`
- `currency`
- `availability`
- `description`
- `category`
- `brand`
- `average_rating`
- `reviews_count`
- `images`
- `product_details`
- `scraped_at`

The notebook creates cleaned and engineered datasets under:

```text
data/modified/
```

Key generated files include:

```text
data/modified/etsy_master.csv
data/modified/etsy_regression.csv
```

## Repository Structure

```text
.
├── analysis.ipynb
├── data/
│   ├── etsy.csv
│   └── modified/
│       ├── etsy_master.csv
│       └── etsy_regression.csv
├── viz/
│   ├── task1_social_impact/
│   ├── task2_sentiment/
│   ├── task3_emotion/
│   ├── task4_eda/
│   └── task5_regression/
├── models/
├── outputs/
│   ├── regression_table_all.csv
│   └── model_final_summary.txt
└── README.md
```

## Requirements

The notebook uses the following Python libraries:

```text
pandas
numpy
nltk
matplotlib
seaborn
scikit-learn
statsmodels
textstat
nrclex
sentence-transformers
IPython
```

Install the main dependencies with:

```bash
pip install pandas numpy nltk matplotlib seaborn scikit-learn statsmodels textstat nrclex sentence-transformers ipython
```

The notebook also downloads the VADER lexicon:

```python
nltk.download("vader_lexicon")
```

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/suryamothukuri/etsy-retail-marketing.git
cd etsy-retail-marketing
```

2. Install dependencies:

```bash
pip install pandas numpy nltk matplotlib seaborn scikit-learn statsmodels textstat nrclex sentence-transformers ipython
```

3. Make sure the raw data file exists at:

```text
data/etsy.csv
```

4. Open the notebook:

```bash
jupyter notebook analysis.ipynb
```

5. Run all cells from top to bottom.

The notebook will create the modified datasets, visualizations, regression tables, and final model summary.

## Notes

- This is an observational analysis, so the regression results should be interpreted as associations rather than causal effects.
- The `SocialImpact`, `Handmade`, `personalization`, and `trust_factor` variables are rule-based text indicators. Their quality depends on the accuracy and coverage of the regular-expression patterns.
- Review count is used as a proxy for listing popularity or demand, but it may also reflect listing age, seller history, marketplace ranking, or other unobserved factors.
- Category controls are included to reduce confounding from product-type differences.

## Project Summary

This project finds that trust-building language and positive sentiment are the strongest positive predictors of Etsy listing popularity in the final model. Lexical diversity, handmade language, and price are negatively associated with review count after controls. Social-impact language is rare in the dataset and does not show a statistically significant association with popularity in the final model.
