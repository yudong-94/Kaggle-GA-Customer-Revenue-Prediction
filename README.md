# Kaggle-GA-Customer-Revenue-Prediction

This is the code repo of the Google Analytics Customer Revenue Prediction Competition

Please notice that this is my code for the competition before its relaunch in early Nov. (There is a data leakage identified in late Oct, so everything about this competition has been modified, including rule, dataset, and prediction objectives... And due to time availability, I decided not to continue with the competition.)

**Dataset**: Google Analytics data of Google Merchandise Store website. It's visit-level data, including userid, time, geo_info, pageviews, hits, referrer, ad_click, ...

**Objective**: Predict the total purchase a user has made during the visits in the test set.

**Mothodology**: 
1. I mainly used tree-based models including Catboost and LightGBM. The reason to choose these two is that tree-based models are generallt more robust in prediction, and these two models have been proven to be more efficient in traning (as I am using my personal laptop to train the models and only available to do feature engineering after work). Specifically for Catboost model, this is the first time I tried this model, and its characteristic of handling with categorical variables automatically is a huge pro.  
2. I conducted 5-fold cross validation on visit-level revenue. Although the target is to predict user-level revenue, as the dataset is largely imbalanced (only a very small portion of users have made purchase during the visit), and this dataset is not the complete history of each user's visit to the site, these two cross validation schema should not outperform one another theoretically.  
3. As always, I spent a lot of time on feature engineering, mostly on how to group the categories on categorical variables (since some of the variables have hundreads of levels), how to transform categorical variables (though it's handled automatically with Catboost), and how to generate new variables.  
4. I don't regard it as a time-series prediction problem, becuase as I mentioned, it's a small sample of some users' incomplete visit records, and users typically do not appear multiple times in the dataset. Though time-based features still play a great role in prediction, because during certain time of the day/week/year, people are definitely more likely to make a purchase.  
5. I planned to Ensemble the models, but didn't get a chance to do that, as the competition is paused and modified before I got to that step...  


Overall it's a nice learning experience :) As I have been playing with the Adode Analytics data everyday at work to understand user behaviors, It's actually great to have a chance to try predicting sales with those web data from Google Analytics, which comes in very similar format as Adobe Analytics data. Though the data leakage accident prevented me from completing the competition in the end...


