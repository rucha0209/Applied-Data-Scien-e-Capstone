# Applied-Data-Science-Capstone-

## Business Problem
Cologne, the city the author lives in, attracts a large number of tourists, not least due to its famous cathedral, the trade fairs and conventions, such as the gamescom, and its vibrant party scene. 
For tourists, finding the right place to eat can be a challenge, though. German dishes include a lot of meat, often pork, which many people do not want to eat for health-related, religious, cultural or moral reasons. This is just one motive for giving tourists a good overview about what to eat where.

Thus, the goal I want to reach with this exercise is to give a simple recommendation to tourists in Cologne: in which district of the city will you find a large number or even concentration of which types of restaurants? Where to eat Mediterranean food, where to find German food, where to get fast food? The target audience are foreign tourists.


## Data Description
I will, as requested by the assignment task, use foursquare data about restaurants in Cologne. Foursquare is a US tech company from New York focusing on location data. Their technology and data powers apps such as Apple's Maps, Uber, Twitter and many other household names. 

Here is an example of a vegetarian restaurant in Cologne on foursquare: https://de.foursquare.com/v/sattgr%C3%BCn/5c33306cc824ae002c2b414c. I will use foursquare data such as the restaurant name, ID, location and category of food (vegetarian, Italian etc.).

Also, I will use the overview of districts/city parts of Cologne from Wikipedia: https://en.wikipedia.org/wiki/Districts_of_Cologne

## Methodology
I scraped data from Wikipedia to create a dataframe with the city districts of Cologne: https://en.wikipedia.org/wiki/Districts_of_Cologne. For this, I used the pandas read function. I had to clean the resulting data frame in terms of unnecessary information or data that could not be handled in a data frame, such as picture data of the coat of arms of each district. The result is a nice data frame:

Then, I enabled geopy functions by installing the conda-forge geopy package. I used the nominatim function to add geospatial data to the data frame, that is the latitude and the longitude.

Now, foursquare data comes into play. I first did a view try-outs for the city district "Innenstadt", which I know pretty well, to see if the venues retrieved from foursquare seem reasonable and correct. That was the case.

Then, retrieved the foursquare data for all venues on foursquare with a distance of less than 3000 meters from each center of each city district, as indicated as blue dots in the map above. The result was a list of 757 venues all over Cologne city. Out of these 757 venues, 184 where restaurants. These 184 restaurants come from 35 unique restaurant categories, such as Italian, Vietnamese or German.

I plotted a bar chart with the frequency of the 10 most frequently occuring restaurants in the whole city, using seaborn/matplotlib packages. We can see that Italian, German and Turkish restaurants are the most frequently occuring restaurants in Cologne, which seems pretty reasonable, as Germany has a relatively high proportion of people with Italian and Turkish roots, and these cuisines being excellent and highly appreciated by large parts of the population - think about pizza, pasta or kebap!
![image](https://user-images.githubusercontent.com/77296591/117581853-02ff4480-b0cd-11eb-8184-4cda252e0cbf.png)


To find clusters of restaurant types in the different city districts, I first transformed the data frame with the restaurant venues, associated to city districts, by one-hot encoding (0/1).

Than I grouped them, than i used most restaurants venue types for each city district.
I could finally run an unsupervised machine learning algorithm, more specifically, a k-means clustering algorithm from the scikit-learn package. One could use the ellbow method to systematically define the k value, but I simply chose k to be 5, having been inspired by one of the coursera courses to do so.

## Results

Following are the results of Cluster:

CLuster 1
![image](https://user-images.githubusercontent.com/77296591/117581779-908e6480-b0cc-11eb-9875-746867d92c67.png)

Cluster 2
![image](https://user-images.githubusercontent.com/77296591/117581815-bfa4d600-b0cc-11eb-96e6-0e7014c1db66.png)

Cluster 3
![image](https://user-images.githubusercontent.com/77296591/117581825-cfbcb580-b0cc-11eb-9c64-2b63e741f88e.png)

Cluster 4
![image](https://user-images.githubusercontent.com/77296591/117581832-de0ad180-b0cc-11eb-9099-24201c3c0412.png)

Cluster 5
![image](https://user-images.githubusercontent.com/77296591/117581838-eb27c080-b0cc-11eb-9c77-b6a32e2d486c.png)

## Discussion

If I reflect the work necessary to create these results, what comes to my mind is that for typical ways of scraping, cleaning, handling, transforming and visualizing data, all the tools are simply there. We just have to get to know the available open source packages and learn how to use them.

## Conclusion

We ahve achieved the results. This is just one example of fantastic data science uses cases one can realize applying technology which is available for free today! What a time to be alive.

## REferences

https://en.wikipedia.org/wiki/Districts_of_Cologne

https://de.foursquare.com/v/sattgr%C3%BCn/5c33306cc824ae002c2b414c
