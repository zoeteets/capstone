# Capstone for Nashville Software School Data Analytics Program

Completion date: August 19, 2022      

## Table of Contents
1. [Overview](#overview)
2. [Data Question](#dataquestion)
3. [Methodology](#methodology)
4. [Technologies](#technologies)
5. [Data Sources](#datasources)
6. [Conclusion](#conclusion)

<a name="overview"></a>
## Overview
  The Academy of Motion Picture Arts and Sciences holds an annual ceremony, commonly known as The Oscars, to honor movies that premiered in theaters the previous year. For all categories excluding Best Picture, voters are contained to that field (i.e. actors vote for Best Actor, directors vote for Best Director, and so on). Best Picture is the only category in which all Academy members, currently standing at 10,000 members, get to submit a vote. Since the pool of voters is more diverse than other categories, I began to wonder what the data could tell us about how the winner for Best Picture is chosen. For this analysis, I focused on Best Picture nominees in years 1970 - 2020 (300 movies) and their gross revenue.
<a name="dataquestion"></a>
## Data Question
  What is the relationship between gross revenue and winning an Oscar for Best Picture?
<a name="methodology"></a>
## Methodologies
  #### Gathering the Data
  Using Python, I scrapped oscars.org for nominees, producers, years, and winner designation using loops to grab html elements and convert them into dictionaries for manipulation. It was crucial that I used a dictionary for this scrape so that I could identify a single winner from nominees for each year. I then created a combination of user defined functions and loops to repeat the scrape through multiple pages of the website. From there, I was able to transform these dictionaries into a single data frame. 
  To pull in data regarding movie details such as summary, rating, runtime, release year, and gross revenue, I used loops to scrape imdb.com and create a series of lists that were combined into a data frame. I repeated similar steps as with oscar.org and created a user defined function combined with loops to iterate through multiple pages.
  For both websites, I collected data on the entirety of the oscars history from 1929-2022.
  
  #### Cleaning the Data
  Data cleaning was needed when I discovered that The Academy of Motion Pictures has a number of movies under a different title than IMDB. I used regular expressions, data validation techniques, and fuzzy merges to clean and combine the data into a single data frame. Curious about the number of producers and title length, I used regular expressions to separate data that was comma delimited and funtions to create new columns based on calculations of the the cell values.

  #### Analyzing the Data
   After looking at the intial data, I decided to limit the number of years to 1963 - 2020, and later limited it to 1970-2020 to look at the gross revenue across decades. I chose 1963 initially because that was the year The Academy created the category as we know it of "Best Picture". Additionally, it's worth noting that diversity and membership count increased after 1963 resulting in a larger voter pool. 
    In order to properly compare gross revenue over time, I imported the annual consumer price index (CPI) from US Bureau of Labor Statistics and used the following calculation to adjust for inflation: adjusted gross = (original gross / 2020 annual CPI) * original annual CPI. For consistency, I adjusted all gross revenue to the CPI of the final year of analysis (2020). 
    I explored grouping and aggregations on the gross revenue as well as producer number, rating, runtime, genre number, and title length to explore which variable may have the biggest impact on winning the award for Best Picture.

  #### Visualizing the Data
   I utilized seaborn FacetGrids and matplotlib to create preliminary visualizations and then moved to Tableau to create visualizations that were more readable and understandable to the viewer. I imported the data into Tableau and created area charts and scatter plots to analyze the relationship between gross revenue and winning an award. I initially started with all 50 years, but found greater insight when breaking these years up into decades. 

<a name="technologies"></a>
## Technologies
Python - pandas, numpy, seaborn, matplotlib

Tableau - visualizations
<a name="datasources"></a>
## Data Sources
  #### Webscraping
      * www.IMDB.com
      * www.oscars.org
  
  #### Imported
      * Annual Consumer Price Index from U.S. Bureau of Labor Statistics
<a name="conclusion"></a>
## Conclusion
  In the 50 years analyzed, never has a movie won Best Picture if it was the lowest grossing nominee for that year. Looking at winners and maximum gross, the most often a movie with the highest gross of all nomineees won Best Picture was during the 1980's with only 50% of the time. However, when we get to 2010 - 2020, the percent of movies that won with highest gross of all nominees that year drops to 0%. This makes a total of 4.6% of movies in the last 50 years have both the highest gross and receive the award for Best Picture. Upon further research into the changes of 2010, I found that The Academy changed the voting method from a single choice ballot to ranked choice voting. We can conclude three observations from this analysis: 
  1) The lowest grossing movie is not the Best Picture
  2) The Academy and movie-goers value different movies
  3) The highest grossing movie that wins Best Picture beats the odds
