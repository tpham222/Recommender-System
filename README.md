# Recommender-System
A capstone project where a subset of the Amazon dataset was explored and used to create a recommender system.
## Summary
This project started off by importing the data and then applying some cleaning and filtering methods on the dataset. Exploratory data analysis was then performed on the the reviewerID, itemID, rating, and reviewTime columns in order to understand the data better. A recommender system was implemented by applying matrix factorization through the scikit Surprise SVD algorithm. The recommender system allowed for the top 5 items with the highest predicted ratings to be recommended for any specific reviewer.
## Steps 
The steps taken to complete this project are as follows:  

1.) [Data Wrangling](https://github.com/tpham222/Recommender-System/blob/master/notebooks/1%20-%20Data%20Wrangling.ipynb)
- The Amazon dataset was provided by a UCSD Professor named Julian McAuley. The data was imported into python using the Pandas read_json method and was cleaned and prepped for exploratory data analysis. 

2.) [Exploratory Data Analysis](https://github.com/tpham222/Recommender-System/blob/master/notebooks/2%20-%20Exploratory%20Data%20Analysis.ipynb)
- The columns of reviewerID, itemID, rating, and reviewTime were looked at for the EDA. Visualizations were made and potential areas to explore were identified. 

3.) [Deeper Analysis](https://github.com/tpham222/Recommender-System/blob/master/notebooks/3%20-%20Deeper%20Analysis.ipynb)
- Some of the results of interest from the exploratory data analysis were more deeply analyzed. 

4.) [Recommender System](https://github.com/tpham222/Recommender-System/blob/master/notebooks/4%20-%20%20Recommender%20System.ipynb)
- The scikit Surprise package was used in order to implement matrix factorization on the Amazon dataset with the SVD algorithm. 

## Results
The results of this capstone project are presented in a pdf report: [Recommender System Report](https://github.com/tpham222/Recommender-System/blob/master/Capstone%20Project%202%20-%20Final%20Report.pdf). The Jupyter notebooks goes into the more technical details of each step.
### Summary of results  
From the exploratory data analysis it was seen that the average ratings of reviews were very dynamic over the years. The average ratings for this dataset started off at its peak in 2000 with a rating of about 4.39. It then steadily declined over the years until it reached its lowest average rating of 3.88 in 2005. The rating started to steadily increase for about 3 years. Following that was 4 years of relatively static movement of rating values of around 4.10. Upon deeper analysis it was seen that the proportion of ratings explained a lot of the dynamic movements. In particular, the ratings of 1 and 5 had the most movement and their proportions can be seen to affect the average ratings over the years plot.  

The time series plots of count of reviews, count of unique reviewers, and count of unique items over the years revealed that all of them showed exponential growth. A log transformation on the count of reviews was performed and a linear regression line was fit to that plot. The fitted line had an R<sup>2</sup> value of 0.962, which meant that about 96% of the total variance in the log of count of reviews could be explained by the year value.

The scikit Surprise package was used in order to implement a recommender system with matrix factorization. The model that Surprise provided which closely resembled matrix factorization was SVD. With GridSearchCV, the following hyperparameters that provided the lowest RMSE score with the SVD model on the Amazon dataset were: lr_all=0.01, reg_all=0.5. With these hyperparameters, the entire dataset was fitted to the model and then 5-fold cross-validation was performed. The results showed that the average RMSE value for the 5 folds was 1.094 with a standard deviation of 0.0026. This meant that there was very little difference in RMSE values between the folds and that the model performed equally well on different subsets of the data. With the model fitted, the recommender system is now able to predict ratings for any reviewer/item pair. A list of all the items a specific user has yet to rate can be fed into the recommender system in order to get predicted ratings for all of them. The top 5 items with the highest predicted ratings can be recommended to that specific user.
## Author
Thompson Pham
