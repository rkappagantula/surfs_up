# Surfs_Up

## Overview
This project consisted on analyzing weather data from Oahu, Hawaii to support a Surf and Ice-cream shop investment proposal. The analysis consisted on determining whether the seasons could affect the surf and ice-cream business.

## Resources
- Data resources: 
  - hawaii.sqlite

- Software used: 
  - Python
  - SQLAlchemy
  - SQLite

## Results
Statistical results of the precipitation and temperature of the two most active and important months across the years as follows:
![image](https://user-images.githubusercontent.com/96051648/154567394-a1e510b4-6256-4b66-ba57-b2b990dcf960.png)

![image](https://user-images.githubusercontent.com/96051648/154567479-46674ff2-b6e6-4fd1-9fdc-24bb8f5d5fbe.png)

![image](https://user-images.githubusercontent.com/96051648/154567552-0e171e71-7bbb-47d5-afb8-dccd7c58c98b.png)

![image](https://user-images.githubusercontent.com/96051648/154567606-c7a3bf8d-2553-4f44-b275-7e6911546aac.png)

- The average temperature for both June and December are considered good weather suitable for ice-cream (71°F and 74.0°F).
- December happens to have a max precipitation of 6.4mm which is considered heavy rain. The max precipitation for June happens to be 4.4mm which is considered medium-high. This data is not enough to determine the impact on the business.
- June happens to be the most profitable time of the year as the distribution of the weather is more suitable for surfing and ice-cream sales. 

## Summary

The results were found by querying the SQLite database from the Jupyter notebook to then use the `describe()` function to get the statistical analysis. 

### For June Temps

  results = []
  
  results = session.query(Measurement.tobs).filter(extract('month', Measurement.date) == 6).all()
  
  june_df = pd.DataFrame(results, columns=['June Temps'])
  
  june_summary_df = june_df.describe()
  
  june_summary_df

 ### For Dec Temps

  results = []
  
  results = session.query(Measurement.tobs).filter(extract('month', Measurement.date) == 12).all()
  
  dec_df = pd.DataFrame(results, columns=['Dec Temps'])
  
  dec_summary_df = dec_df.describe()
  
  dec_summary_df

  ### For June Precipitation
  
  prcpt_june = []
  
  prcpt_june = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
  
  p_june = pd.DataFrame(prcpt_june, columns=['June Precipitation'])
  
  stats_prcpt_june = p_june.describe()
  
  stats_prcpt_june

  ### For Dec Precipitation
 
  prcpt_dec = []
  
  prcpt_dec = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
  
  p_dec = pd.DataFrame(prcpt_dec, columns=['December Precipitation'])
  
  stats_prcpt_dec = p_dec.describe()
  
  stats_prcpt_dec
