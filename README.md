Social Media Engagement Analytics

Python for Data Analysis | Module-End Assignment 5:

Overview:

This project analyses engagement on 5,000 social media posts using Python. It covers the full workflow: loading and cleaning the raw data, 
exploring it with Pandas, building a few new metrics, running descriptive statistics, and visualising the results with Matplotlib, Seaborn 
and Plotly. The notebook ends with findings on content performance, user trends, behaviour and sentiment.

Repository Contents:

File	Description:
social_media_engagement_analytics.ipynb	Main notebook with code, outputs, charts and explanations
social_media_engagement_5000.csv	Dataset provided with the assignment
README.docx	This file

Dataset:

The file has 5,000 rows and 19 columns, covering posts from January 2022 to December 2023.
Group	Columns
User	user_id, age, gender, country, follower_count, is_verified
Post	post_id, post_type, post_category, hashtags, posted_at, device_type
Engagement	likes, comments, shares, watch_time_sec, impression_count, engagement_rate

Other	sentiment:
Note: engagement_rate in the source is a fraction (likes + comments + shares divided by impressions), not a percentage. I converted it to a
percentage in a new column, engagement_rate_pct, and use that throughout.

Tools Used:
•Python 3, Pandas, NumPy for cleaning, wrangling and statistics

•Matplotlib and Seaborn for static charts

•Plotly for interactive charts

•Google Colab / Jupyter Notebook for running everything

How to Run:
•Download the notebook and the CSV and keep them in the same folder.

•Open the notebook in Jupyter or upload both files to Google Colab.

•Install the libraries if needed:

pip install pandas numpy matplotlib seaborn plotly

•Run all cells from top to bottom. The notebook reads the CSV by its file name, so do not rename it.

What Was Done:

Task 1:

Import and setup. Loaded the CSV, checked data types, and converted posted_at from dd-mm-yyyy text to datetime.

Task 2:

Cleaning. Handled missing values, removed duplicates, standardised categories, fixed unrealistic values and extracted hashtag counts.
Details are in the table below.

Task 3: 

Exploration. head, tail, info, describe, value counts, a correlation matrix and groupby summaries.

Task 4: 

Wrangling. Merged a country-to-region lookup, and created engagement_score, log-transformed metrics and hashtag_count. Summaries by post
type, country and sentiment.

Task 5:

Statistics. Mean, median, mode, standard deviation, variance, percentiles, skewness and kurtosis for likes, comments, shares, watch time,
engagement rate and followers.

Task 6:

Visualisation. Six Matplotlib charts, six Seaborn charts and three interactive Plotly charts (15 in total).

Data Cleaning Summary:

Issue found	Where	How it was handled:

Missing values (150 each)	age, gender, likes, comments, shares, sentiment	Median for age, mode for gender and sentiment, 0 for likes, comments and shares

Repeated post_id (9 rows)	post_id	Kept the first occurrence of each id

Rates above 100% (3 rows)	engagement_rate	Capped at 1 (100%)

Extreme comment counts	comments	Capped at the 99.5th percentile

Negative counts	likes, comments, shares	None found; check is in the code in case of other data

Text categories	gender, post_type, device_type, sentiment	Already consistent; trimmed and title-cased for safety
After cleaning the dataset has 4,991 rows.


Key Findings:
All engagement rates below are averages of engagement_rate_pct.

Content performance

•Post types are very close. Text (37.6%) and Video (37.6%) lead, followed by Image (37.3%). Reels are lowest at 36.0%.

•Fitness has the highest engagement rate (38.3%), followed by Music (38.0%) and Education (37.8%). Food is lowest (35.7%). Music gets the most likes per
post on average.

•Australia has the highest average engagement rate (39.4%), then Japan (38.5%) and the UAE (38.3%). India is lowest (34.0%).
User trends

•Age has almost no effect (correlation with engagement rate is -0.03). The 30 to 39 group is slightly highest (38.6%) and 50 to 64 is lowest (36.0%).

•Verified accounts get slightly more impressions on average (about 50,700 vs 50,000) but a lower engagement rate (34.9% vs 37.4%). Reach does not translate

into more engagement per impression.

Behavioural insights:

•The dataset only records the date, not the time of day, so best time of day cannot be answered directly. By weekday, Tuesday gets the most impressions 

(about 51,300) and Thursday the fewest (about 48,100). By month, September is highest.

•Mobile has the highest average watch time (about 4,088 seconds), slightly ahead of tablet (3,981) and desktop (3,976). The gap is small.

Sentiment

•Negative (37.5%) and neutral (37.4%) posts have a slightly higher engagement rate than positive posts (36.8%). Positive is the biggest group by count 

(2,508 posts).

•Neutral posts get the fewest likes on average (about 9,627 vs about 9,880 for the other two).

Overall driver

•Engagement rate moves mostly with impressions (correlation -0.78) and likes (0.38). This is expected because it is calculated from them: posts with fewer 

impressions show a higher rate.

Limitations

•Differences between most groups are small, usually under two percentage points. They are worth noting but not strong enough to base decisions on without

significance testing.

•Missing likes, comments and shares were filled with 0, which may slightly understate engagement.

•Time-of-day analysis was not possible because posted_at has no time component.
