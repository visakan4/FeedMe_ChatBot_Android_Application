# FeedMe

## Project description

Yelp user reviews and ratings clearly play a major role in determining the fortune of a business as two professors Michael Anderson and Jeremy Magruder from university of California, Berkeley found that “restaurants with a rating improved by just a half a star on a scale of 1 to 5 was much more likely to be full at peak dining times”. However, it gets difficult and time consuming for users to read each review manually and identify the restaurants based on their preference. Furthermore, this leads user to make decision based on star ratings which can be misleading as ratings doesn’t provide the context and features on which a restaurant is rated. 

Feed Me is an Android application that recommends restaurants to users by learning and analyzing the user reviews in
YELP dataset. YELP is an open source dataset containing large number of reviews about the restaurants, the
application mainly aims to assist the users in finding the best restaurant under different categories such as ambienece, discount and deals based on the authentic user reviews through voice commands. We have implemented Sentimental Analysis and Topic modelling to predict the star rating of each restaurants. FeedMe app uses built-in speech recoginition API from Google SDK to attain speech to text capabilities. 

## Architecture

![alt text](https://github.com/visakan4/FeedMe_ChatBot_Android_Application/blob/master/Architecture.JPG "Architecture")

## Dataset

**Link**: https://www.yelp.com/dataset

![alt text](https://github.com/visakan4/FeedMe_ChatBot_Android_Application/blob/master/images/datasetSchema.png "Architecture")

## Data preprocessing

Yelp dataset had a total of 5.2 million reviews for 1.7 million businesses. We did not have enough resources to build a model that can process 5.2 million reviews, so we decided to use a subset of the reviews in order to build our model. In order to get a subset of the reviews, we performed three different filters in our dataset. Below we have briefly explained the three filtering mechanisms applied on Yelp dataset.

### Category based filter

Our problem statement concentrated only on restaurants but Yelp dataset contained data about other businesses like shopping market, grocery shops, etc. First step was to filter out the data which were not related to restaurant domain. We made use of “categories” attributes present in the “Business” table to filter the unnecessary categories. We observed that there were a total of 1264 unique categories. We manually went through each and every category and made a list which contained categories specific to restaurants. Using the list, we found the “business_id” for each restaurant from the “business” table. “business_id” is a unique identifier(primary key) assigned to each business in the Yelp dataset. We made use of “business_id” attribute to filter data from other tables.

### Country-based filter:

Even after filtering the data based on categories, we still had 3.2 million reviews and 75,000 businesses. This was still huge data to process, so we decided to filter based on country and make use of the restaurants which were located in Canada. Our dataset did not provide any details about the country of the restaurants, but they contained details like city, latitude and longitude. We performed reverse geocoding using the latitude and longitude to find the country of the restaurants. Once we had obtained the country of each restaurant, we filtered out the restaurants which were not located in Canada.

### Language-based filter:

After applying Country and Category based filter, we had a total of 25,124 restaurants and approximately 8,000,000 reviews. Reviews tables consisted reviews of various different languages because of this we were not able to get accurate results, so we decided to concentrate on reviews which are in English language alone. We followed a stopword based approach to find the language of each review. We found the number of stopwords present in each review for each language supported by NLTK. We assume that the language which has the most number of stopwords is the language of the review. This method was quite effective and it accurately predicted the language for most of the reviews. Though this approach was not successful for some scenarios where reviews did not contain any stopwords, we manually went through those reviews and filtered it. Once we had detected the language, we filtered out non-English reviews. After all the filtering was done, we had a total of 6,65,000 reviews and 25,124 restaurants.

We made use of IBM DB2 Warehouse and Python packages like pandas, geopy to perform the above-mentioned filters. After filtering, we had uploaded our dataset to IBM cloud Database using batch script.

## Sentimental Analysis



## Topic modelling



## Screenshots



## Installation


