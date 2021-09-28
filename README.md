# Predicting-NBA-Salaries
This project highlights two important skills needed for data science. First is the ability to clean data and second is to create machine learning models.
</br>
</br>
## What are NBA Advanced Statistics?
</br>

According to the [NBA's official stats FAQ](https://www.nba.com/stats/help/faq/), “Advanced Stats are a way to study basketball through objective analysis. It is a more in-depth way to look at a simple box score, and more accurately evaluates the skill and production of a player or team.”
</br>
</br>
## Data
</br>

The data set used in this project comes from [Kaggle](https://www.kaggle.com/aishjun/nba-salaries-prediction-in-20172018-season) by the user Ai Shaojun. This dataset contains advanced and non traditional stats from the 2017-2018 NBA season.
While this data set was perfect for this project, a lot of exporatory data analysis (EDA) needed to be done in order to fully clean and prepare this dataset for machine learning.
</br>
</br>
## EDA and Data Cleaning
</br>
Here is one example that shows EDA and Data Cleaning

</br>

![Screen Shot 2021-08-23 at 1 14 59 AM](https://user-images.githubusercontent.com/85101850/130509674-617f6999-01ec-4ad6-8a3c-e7b339b2519e.png)
</br>
In the NBA, every year they hold a draft where a total of 60 players are picked and added into 1 of 30 NBA teams. Now the problem with this data set is that it lists people being drafted 62nd. Upon further investigation, I realized that the dataset has undrafted players being drafted 62nd. This needed to be fixed, so the solution was to create a new column assigning a 0 if the player was undrafted and a 1 if the player was drafted.

</br>
</br>

## Regression Models
</br>

Building regression models was the next step to this project. Unfortunately, building a linear, KNN, random forest, and XGboosted regression model did not create a good model. When train test splitting the data, the models were all very overfit and yielded really poor R^2 values. I then took the two best models, random forest and XGBoost, and used them within a voting regression model. These were the testing metrics I got out of the model:
</br>

![Screen Shot 2021-08-23 at 1 25 23 AM](https://user-images.githubusercontent.com/85101850/130512816-e2eef7ae-4869-4cce-9266-f83bee1e17cc.png)
</br>

The model has an RMSE of over 4 million which is not very good.
</br>
</br>

## Neural Network
</br>

Using the keras library from tensorflow, I built a neural network to hopefully build a better model. Unfortunately, this was not the case.

</br>

![Screen Shot 2021-08-23 at 1 26 01 AM](https://user-images.githubusercontent.com/85101850/130513263-7f060b1e-5494-4977-90bf-d49957324073.png)

</br>

These were the MSE and RMSE values the model gave me for each epoch it ran. It was set to run 200 epochs but early stopped way before. Even running the model all the way to 200 epochs kept the metrics around the same amount. The neural network built a model that was even worse than the voting regression model with an RMSE of over 5 million.

</br>
</br>

## Conclusion

</br>

While advanced statistics and non traditional statistics are useful for many other reasons, predicting or assigning a player's salary based on those statistics is not one of them.

This is probably why most people use traditional statistics, like points per game, assists per game, 3 point percentage, to predict an NBA player's salary.
