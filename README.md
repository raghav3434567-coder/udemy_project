# Udemy Courses Analysis

An exploratory data analysis (EDA) of 3,672 Udemy courses across four subjects, using **Python, pandas, NumPy, Matplotlib and Seaborn**. The notebook looks at popularity (subscribers, reviews), pricing, course level, subject, free vs paid courses, and an estimated revenue per course.

## Project Structure

```
.
├── udemy_project.ipynb         # Analysis notebook
├── udemy_courses.csv           # Dataset (3,672 rows x 12 columns after de-duplication)
├── Udemy_Project_Report.pdf    # Detailed project report
└── README.md                   # This file
```

> The notebook reads the CSV from `./drive/MyDrive/udemy_courses.csv` (Google Colab with Drive mounted). To run locally, place the CSV next to the notebook and change the path to `udemy_courses.csv`.

## Dataset

| Column | Description |
|---|---|
| course_id | Unique course ID |
| course_title | Course name |
| url | Course link |
| is_paid | True for paid, False for free |
| price | Price in USD (0 to 200) |
| num_subscribers | Number of enrolled students |
| num_reviews | Number of reviews |
| num_lectures | Number of lectures |
| level | All Levels, Beginner, Intermediate or Expert |
| content_duration | Course length in hours |
| published_timestamp | Publication date and time |
| subject | Business Finance, Graphic Design, Musical Instruments or Web Development |

## What the Notebook Does

1. Loads the data, drops duplicates and checks for nulls (none found).
2. Summarises numeric columns and counts free vs paid courses.
3. Finds the courses with the most subscribers, reviews, lectures and longest duration.
4. Measures correlation of price with reviews and with subscribers.
5. Compares subjects and levels by course count, average and total subscribers.
6. Compares paid and free courses.
7. Creates an estimated `revenue` column (`num_subscribers * price`) and compares it by subject and level.
8. Counts Python-related courses and lists the 10 most popular.

## Key Results

| Metric | Result |
|---|---|
| Courses / columns | 3,672 / 12 |
| Paid / free courses | 3,362 / 310 |
| Mean price / subscribers | $66.10 / 3,191 |
| Most subscribers | Learn HTML5 Programming From Scratch (268,923) |
| Most reviews | The Web Developer Bootcamp (27,445) |
| Highest estimated revenue | The Web Developer Bootcamp ($24.3M) |
| Most popular subject | Web Development (7.98M total subscribers) |
| Most popular level | All Levels (6.92M total subscribers) |
| Avg subscribers: free vs paid | 11,534 vs 2,430 |
| Python-related courses | 29 |
| Correlation: price vs subscribers | 0.05 |
| Correlation: subscribers vs revenue | 0.56 |

## How to Run

```bash
pip install numpy pandas matplotlib seaborn jupyter
jupyter notebook udemy_project.ipynb
```

Python 3.12+ is recommended, because the notebook nests same-type quotes inside f-strings.

## Known Limitations

- The paid vs free bar chart uses hard-coded counts with the labels swapped (shows 310 for "Paid Course" when 310 is the free count).
- The "total reviews by subject" cell sums `num_subscribers`, not `num_reviews`.
- Revenue is only an estimate (subscribers x list price). It ignores discounts, refunds and Udemy's revenue share.
- Correlations of 0.35 and 0.56 are described as "negligible" and "mediocre"; they are better described as weak-to-moderate.
- `seaborn` is used before it is imported, and some outputs (3,368 paid courses vs 3,362) suggest cells were run out of order.
- The Python search is case-sensitive.

See `Udemy_Project_Report.pdf` for details and recommended fixes.

## Tech Stack

Python, pandas, NumPy, Matplotlib, Seaborn, Jupyter / Google Colab
