

## FakeNewsNet

*** We will never ask for money to share the datasets. If someone claims that s/he has the all the raw data and wants a payment, please be careful. ***

***We released a tool [FakeNewsTracker], for collecting, analyzing, and visualizing of fake news and the related dissemination on social media. Check it out!***

***The latest dataset paper with detailed analysis on the dataset  can be found at [FakeNewsNet]***

**Please use the current up-to-date version of dataset**

Previous version of the dataset is available in branch named `old-version` of this repository.


## Overview  

Complete dataset cannot be distributed because of Twitter privacy policies and news publisher copy rights.  Social engagements and user information are not disclosed because of Twitter Policy. This code repository can be used to download news articles from published websites and relevant social media data from Twitter. 

The minimalistic version of latest dataset provided in this repo (located in `dataset` folder) include following files:

 - `politifact_fake.csv` -  Samples related to fake news collected from PolitiFact 
 - `politifact_real.csv` -  Samples related to real news collected  from PolitiFact 
 - `gossipcop_fake.csv` - Samples related to fake news collected from GossipCop
  - `gossipcop_real.csv` - Samples related to real news collected from GossipCop

Each of the above CSV files is comma separated file and have the following columns

 - `id` - Unique identifider for each news
 - `url` - Url of the article from web that published that news 
 - `title` - Title of the news article
 - `tweet_ids` - Tweet ids of tweets sharing the news. This field is list of tweet ids separated by tab.

## Installation    

###  Requirements:
 Data download scripts are writtern in python and requires `python 3.6 +` to run.
 
Twitter API keys are used for collecting data from Twitter.  Make use of the following link to get Twitter API keys    
https://developer.twitter.com/en/docs/basics/authentication/guides/access-tokens.html   

Script make use of keys from  _tweet_keys_file.json_ file located in `code/resources` folder. So the API keys needs to be updated in `tweet_keys_file.json` file.  Provide the keys as array of JSON object with attributes `app_key,app_secret,oauth_token,oauth_token_secret` as mentioned in sample file.

Install all the libraries in `requirements.txt` using the following command
    
    pip install -r requirements.txt


###  Configuration:

 FakeNewsNet contains 2 datasets collected using ground truths from _Politifact_ and _Gossipcop_.  
    
The `config.json` can be used to configure and collect only certain parts of the dataset. Following attributes can be configured    
  
 - **num_process** - (default: 4) This attribute indicates the number of parallel processes used to collect data.    
 - **tweet_keys_file** - Provide the number of keys available configured in tweet_keys_file.txt file       
 - **data_collection_choice** - It is an array of choices of various parts of the dataset. Configure accordingly to download only certain parts of the dataset.       
   Available values are  
     {"news_source": "politifact", "label": "fake"},{"news_source": "politifact", "label":    "real"}, {"news_source": "gossipcop", "label": "fake"},{"news_source": "gossipcop", "label": "real"}  
  
 - **data_features_to_collect** - FakeNewsNet has multiple dimensions of data (News + Social). This configuration allows one to download desired dimension of the dataset. This is an array field and can take following values.  
	              
	 - **news_articles** : This option downloads the news articles for the dataset.  
     - **tweets** : This option downloads tweets objects posted sharing the news in Twitter. This makes use of Twitter API to download tweets.  
     - **retweets**: This option allows to download the retweets of the tweets provided in the dataset.  
     - **user_profile**: This option allows to download the user profile information of the users involved in tweets. To download user profiles, tweet objects need to be downloaded first in order to identify users involved in tweets.  
     - **user_timeline_tweets**: This option allows to download upto 200 recent tweets from the user timeline. To download user's recent tweets, tweet objects needs to be downloaded first in order to identify users involved in tweets.
     - **user_followers**: This option allows to download the user followers ids of the users involved in tweets. To download user followers ids, tweet objects need to be downloaded first in order to identify users involved in tweets.  
     - **user_following**: This option allows to download the user following ids of the users involved in tweets. To download user's following ids, tweet objects needs to be downloaded first in order to identify users involved in tweets.




