# Midwinter radar imaging establishes first breeding population baseline for the endangered emperor penguin

Dataset DOI: [10.5061/dryad.ngf1vhj9j](https://doi.org/10.5061/dryad.ngf1vhj9j)

## Description of the data and file structure

This repository contains the data and code required to recreate the analysis and results from our paper, "Midwinter radar imaging establishes first breeding population baseline for the endangered emperor penguin". We tasked high resolution (0.25 - 1.0 m resolution) Synthetic Aperture Radar (SAR) imagery of all emperor penguin breeding colonies through the winter (April - August) 2025 and estimated the number of breeding pairs captured in the mid winter imagery to estimate the first global breeding population baseline. 

<br />

We first delineated the huddle areas in the SAR imagery in ArcGIS Pro. We then extracted ERA5 weather data for each date and location for each image to use in a the Winterl et al. (2024) windchill model. Using this windchill model, we  estimated the huddle density (number of penguins per m2) and used these values estimated the number of individual birds captured in each image. We determined the phenological stage of the birds by considering the date of the imagery, as well as the huddle appearance: tightly aggregated huddles capture in late June/July that covered less area than huddles from earlier in the winter were considered to represent only males being present.  Using the imagery of the 'male huddle' phase, we estimated the number of breeding pairs at each site (n = 55). 

<br />

We validated our analysis using chick counts from 7 locations. For this analysis, we included data from a proof of concept study, that looked at emperor penguin huddles at six sites in 2024 (LaRue et al. 2026). We had 10 site-year pairs where we acquired both wintertime SAR-derived breeding pairs estimates and springtime chick counts. We compared our SAR-derived breeding pair estimates with chick counts to determine whether the density model was accurately estimating how many males were there in the middle of winter. 

<br />

We further compared our SAR-derived breeding pair estimates to what was previously known of colony sizes from springtime optical imagery analysis. For this analysis, we extracted springtime abundance estimates from the three studies that have conducted such analyses at circumpolar or regional scales (LaRue et al. 2024, Fretwell et al. 2025, Foster-Dyer et al. 2026). We selected the longest time series available for comparison. 

### Files and variables

#### File: dfHuddle_export_combined_uncertainty.csv *and*

**Description:** This file contains the estimated number of breeding pairs derived from the male huddle imagery for all colonies in 2025. It includes the colony name, location, date range of imagery, number of observations, and the mean and median counts. It also includes the two sources of uncertainty and the combined uncertainty value. The file presents the number of breeding pairs that are reported in the publication.

#### File: dfHuddleMLR_export_combined_uncertainty.csv

**Description:** This file contains the estimated number of breeding pairs derived from the male huddle imagery for the six sites that were sampled in 2024 (LaRue et al. (15). The file includes the colony name, location, date range of imagery, number of observations, and the mean and median counts. It also includes the two sources of uncertainty and the combined uncertainty value. These two datasets contain the same columns and rows. 

| Variables         | Definition                                                                                                                                                                                                                                                                                           |
| :---------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| colony\_name      | the name of the colony                                                                                                                                                                                                                                                                               |
| lat               | latitude of image task                                                                                                                                                                                                                                                                               |
| lon               | longitude of image task                                                                                                                                                                                                                                                                              |
| date\_first       | date of first image determined to represent the male huddle                                                                                                                                                                                                                                          |
| date\_last        | date of the last image determined to represent the male huddle                                                                                                                                                                                                                                       |
| DOY\_mean         | mean day of year value for the imagery determined to represent the male huddle                                                                                                                                                                                                                       |
| n\_obs            | number of images per location that were classed as male huddle                                                                                                                                                                                                                                       |
| uncertainty\_flag | qualitative determinate of quality of estimate based on number of observations, single obs = 1, low n = 2, good = >3                                                                                                                                                                                 |
| count\_mean       | mean number of individuals estimated using the density model across all imagery that was determined to be male huddle for that location                                                                                                                                                              |
| count\_median     | median number of individuals estimated using the density model across all imagery that was determined to be male huddle for that location (we used mean as some locations had only one or two estimates and median was not able to be used across all sites)                                         |
| coeff\_lower      | lower coefficient uncertainty (values reported in Winterl et al. 2024), same values were applied to all observations                                                                                                                                                                                 |
| coeff\_upper      | upper coefficient uncertainty (values reported in Winterl et al. 2024), same values applied to all observations                                                                                                                                                                                      |
| coeff\_se\_pm     | the plus or minus standard error calculated for each estimated density based on the coefficient uncertainty reported in Winterl et al. 2024                                                                                                                                                          |
| obs\_std          | standard deviation of the number of individuals estimated from 'male huddle' observations, indicating variability between observation. Only available if more than one male huddle image was captured                                                                                                |
| obs\_sem          | standard error around the mean of the number of individuals estimated from 'male huddle' observations, indicating uncertainty in breeding estimate based on how many images were captured, only available if more than one male huddle image was captured                                            |
| obs\_lower        | lower bounds of the observation based uncertainty interval, calculated by minusing obs\_sem from count\_mean                                                                                                                                                                                         |
| obs\_upper        | upper bounds of the observation based uncertainity interval, calculated by adding obs\_sem to count\_mean                                                                                                                                                                                            |
| combined\_lower   | lower bounds of combined uncertainity, calculated by minusing combined\_se\_pm from count\_mean                                                                                                                                                                                                      |
| combined\_upper   | upper bounds of the combined uncertainty, calculated by adding combined\_se\_pm to count\_mean                                                                                                                                                                                                       |
| combined\_se\_pm  | combined standard error which combined both sources of uncertainty (coefficient uncertainity and observation variance). Values were added in quadrature to produce a more conservation uncertainty estimate. If only one male huddle image was acquired, combined\_se\_pm is equal to coeff\_se\_pm  |
| mean\_range\_pct  | the total combined uncertainty range, indicating a scale-independent measure of relative uncertainty for each colony estimate, calculated by multiplying combined\_se\_pm by 2 and expressed as a percentage of count\_mean                                                                          |

<br />

#### File: EP_Chick_counts.xlsx

**Description:** This file contains the chick count data that were provided by colleagues at the US Antarctic Program (Cape Crozier), the Korea Polar Research Institute (Cape Washington, Cape Roget, and Coulman Island), and the Australian Antarctic Division (Lazarev, Amanda Bay, Astrid Bay, and Taylor Glacier). These data were used in the model validation step.

| Variables     | Definition                                     | <br /> |
| :------------ | :--------------------------------------------- | :----- |
| colony\_full  | full name of colony                            | <br /> |
| colony\_name  | shortened name of colony                       | <br /> |
| site\_id      | four letter code for colony name               | <br /> |
| count         | number of penguins counted                     | <br /> |
| year          | year of count                                  | <br /> |
| date          | date count was undertaken                      | <br /> |
| season        | season count was undertaken                    | <br /> |
| age           | age of the birds counted (adult or chick)      | <br /> |
| credit        | who performed the count and provided the data  | <br /> |
| notes         | additional information about each observation  | <br /> |

<br />

#### File: dfRFD_with_predictions_cleaned_final.csv *and*

#### File: dfMLR_with_predictions_final.csv

**Description:** These file contains the complete dataset summarizing all imagery that had emperor penguin huddles visible. It includes the site names, image IDs, dates and times of each image acquisition, the area covered by the birds in each image, the estimated phenological stage of each image, the satellite covariates (grazing, azimuth, resolution, orbit state etc), the extracted ERA5 weather data for each timestamp and location and the predicted density (rho_pred) and counts based on the predicted density and huddle areas. It also includes the upper and lower density bounds (derived from the coefficient uncertainty) and the resulting upper and lower count bounds. DfMLR_xxyy includes data published from LaRue et al. 2026 and was included to assess model performance in relation to chick counts. 

| Variables        | Definition                                                                                                                                                                                                                                  |
| :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| colony\_name     | colony name                                                                                                                                                                                                                                 |
| site\_id         | four letter code for colony name                                                                                                                                                                                                            |
| group            | group colony is in for arcmap projects                                                                                                                                                                                                      |
| image\_id        | image ID provided by umbra, only including images that were in the right location and could have had birds visible in them                                                                                                                  |
| date             | date image captured                                                                                                                                                                                                                         |
| month            | month image captured                                                                                                                                                                                                                        |
| day              | day image captured                                                                                                                                                                                                                          |
| year             | year image captured                                                                                                                                                                                                                         |
| DOY              | day of year image captures (calculated from date, jan 1st = 1, dec 31st = 365)                                                                                                                                                              |
| lat              | latitude of image task                                                                                                                                                                                                                      |
| lon              | longitude of image task                                                                                                                                                                                                                     |
| avg\_size        | average size of colony based on LaRue et al. 2024 (if discovered by then) or Fretwell et al. 2024 or Wienecke et al. 2024                                                                                                                   |
| area\_m2         | huddle area in m2                                                                                                                                                                                                                           |
| phenology\_est   | estimated phenological stage based on huddle appearance, area covered and date (male huddle, females present, female return)                                                                                                                |
| removed          | indicated if the area calculated for this image was removed, often due to the birds being too dispersed (often after female return) to accurately quantify. Removed data were not analysed and did not contribute to the breeding estimate. |
| observation(1-5) | ease of observation metric                                                                                                                                                                                                                  |
| grazing          | grazing angle of image task                                                                                                                                                                                                                 |
| incidence        | incidence angle of image task                                                                                                                                                                                                               |
| azimuth          | azimuth angle of image task, difference between satellite position and North (0degrees)                                                                                                                                                     |
| resolution       | resolution of image task (0.25m-1m)                                                                                                                                                                                                         |
| looks            | whether image was multilooked or single looked (1 or 2 looks)                                                                                                                                                                               |
| orbit\_state     | whether satellite was ascending or descending                                                                                                                                                                                               |
| polarization     | polarization of image task (VV or HH)                                                                                                                                                                                                       |
| slant\_range     | distance in metres (slant\_range) between satellite and target                                                                                                                                                                              |
| surface\_type    | surface type that birds were located on (fast ice, multi-year ice, ice berg, ice shelf,  rock, glacier)                                                                                                                                     |
| obs              | observation EOO value shortened                                                                                                                                                                                                             |
| date\_time       | date time extracted from image id                                                                                                                                                                                                           |
| time             | time extracted from image id                                                                                                                                                                                                                |
| time\_UTC        | time in UTC                                                                                                                                                                                                                                 |
| date\_UTC        | date in UTC                                                                                                                                                                                                                                 |
| ts               | formatted date time                                                                                                                                                                                                                         |
| met\_ff10        | wind speed clculated from u and v wind components, at 10m above surface using lat long and timestamp, era5 extracted                                                                                                                        |
| temp\_airK       | temperature in Kelvin, at 2m above surface at lat lon and time, era5 extracted                                                                                                                                                              |
| met\_humc        | humidity, calculated from surface pressure, temperature and dew point                                                                                                                                                                       |
| met\_rad         | solar radiation at surface, as our observations occur in winter, most are  0                                                                                                                                                                |
| d2m              | dew point at 2m above surface, used to calculate humidity                                                                                                                                                                                   |
| rh\_water        | relative humidity in relation to water, if temperature is above 0 the relative humidity column uses this value                                                                                                                              |
| rh\_ice          | relative humidity in relation to ice, if temperature is below 0 the relative humidity column uses this value                                                                                                                                |
| rho\_pred        | estimated density of the huddles based on the era5 weather reanalysis data and the windchill model                                                                                                                                          |
| count\_pred      | estimate number of birds calculated by multiply the area of huddles by the predicted density (rho\_pred)                                                                                                                                    |
| rho\_lower       | the lower estimated density bound based on the reported coefficient of each weather coefficient in Winterl et al. 2024                                                                                                                      |
| rho\_upper       | the upper estimated density bound based on the reported coefficient of each weather coefficient in Winterl et al. 2024                                                                                                                      |
| count\_lower     | the lower count bound, calculated by muliplying the rho\_lower by the area of huddles to give the lower uncertainity estimate of number of birds in each image                                                                              |
| count\_upper     | the upper count bound, calculated by multiplying the rho\_upper by the area of huddles to give the upper uncertainity estimate of number of birds in each image                                                                             |
| Ta\_C            | the apparent temperature, the temperature estimated to be experienced by the birds, understanding the effect that windspeed, humidity and radiation has on the temperature                                                                  |

<br />

#### File: est_size_AllColonies.csv

**Description:** This file contains the estimated size of every emperor penguin colony based on springtime observation from the following publications (11, 23–25, 46–48). When multiple estimates were available, we selected the estimated abundance based on the longest time series available, reported in previously published datasets that are also included in the supplementary material.

| Variables    | Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | <br /> |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----- |
| site\_id     | four letter code for colony name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | <br /> |
| colony\_x    | full colony name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | <br /> |
| site\_name   | shortened colony name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | <br /> |
| avg\_size    | average size of that colony based on best available (longest timeseries) data                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | <br /> |
| avg\_size-sd | standard deviation of the average size of the best available estimate                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | <br /> |
| source       | publication that provided the longest time series data for that site                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | <br /> |
| years        | year range that contributed to the average size reported                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | <br /> |
| n\_years     | number of years within the year range that contributed to the estimated average size                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | <br /> |
| method       | method used to estimate the abundance of the site. ("VHR" refers to very high resolution satellite imagery and a bayesian population model, "Sentinel-2" refers to estimated size based on low resolution imagery as high-res is yet to be available for newly discovered colonies, "VHR count" is when individual birds were counted in VHR imagery - not analysed using supervised classification and bayesian model, "VHR estimate" uses the previous linear model approach from Fretwell et al. 2012 that estimates approx. 1 penguin per m2, "Aerial count" refers to on the ground observation of the location, where researchers flew over, took photos and counted the number of birds visible in the photos. \*Note, only "VHR" average size values were compared against our SAR-derived estimates. | <br /> |

#### File: LaRue_etal2024_colony_results09-18.csv *and*

#### File: Foster-Dyer_etal2026_RS_00-2024.csv *and*

#### File: Fretwell_etal2025_WS09-23.csv

**Description:**  These raw data files contributed to the average size analysis to compare our winter SAR-derived breeding adult estimates to the springtime abundance indices previously calculated. Each dataset contains the same covariates. Estimates were derived using a supervised classification of high-resolition optical satellite imagery from spring and a Bayesian population model published in LaRue et al. 2024. The longest timeseries available was extracted for each site and combined with other data sources in the est_size_AllColonies.csv dataset (also uploaded here). 

| Variables    | Definition                                                                                                                                                        | <br /> |
| :----------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----- |
| year         | year of estimate                                                                                                                                                  | <br /> |
| site\_number | site number (referring to colony name)                                                                                                                            | <br /> |
| N\_mean      | estimated number of adult emperor penguins on the ice in springtime derived from colony areas and a bayesian population model                                     | <br /> |
| N\_se        | standard error around the estimated number of adult emperor penguins on the ice in springtime                                                                     | <br /> |
| N\_q025      | lower 2.5% confidence interval for the 95% CI                                                                                                                     | <br /> |
| N\_q05       | lower 5% CI                                                                                                                                                       | <br /> |
| N\_median    | median number of adult emperor penguins on the ice in springtime, derived from colony areas and a bayesian population model                                       | <br /> |
| N\_q95       | upper 5% confidence interval                                                                                                                                      | <br /> |
| N\_q975      | upper 2.5% confidence interval, comtributing to the total 95% CI around the estimated number of adult emperor penguins on the ice in springtime at each location  | <br /> |
| site\_id     | four letter code for the colony name                                                                                                                              | <br /> |
| site\_name   | the name of the colony                                                                                                                                            | <br /> |
| lat          | latitude of the colony (location)                                                                                                                                 | <br /> |
| lon          | longitude of the colony (location)                                                                                                                                | <br /> |

####

#### File: metadata_EP_SAR.xlsx

**Description:** The names and definitions of all variables included in the datafiles uploaded to Dryad and Github.

<br />

#### File: total_population_summary.csv

**Description:** This file contains the combined total number of breeding pairs across the 55 sites that we had midwinter SAR observations of the male huddle in the winter of 2025. The file includes the number of sampled colonies, total count (representing breeding pairs), the two sources of uncertainty and the combined uncertainty.

| Variables             | Definition                                                                                                                                                                                                                                                                                                                                                        | <br /> |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----- |
| description           | total breeding population (all 55 colonies combined)                                                                                                                                                                                                                                                                                                              | <br /> |
| season                | year of estimate 2025                                                                                                                                                                                                                                                                                                                                             | <br /> |
| n\_colonies           | number of colonies estimated                                                                                                                                                                                                                                                                                                                                      | <br /> |
| n\_good               | how many of the 55 colonies had atleast 3 observations of male huddle imagery                                                                                                                                                                                                                                                                                     | <br /> |
| n\_low\_n             | how many of the 55 colonies had only 2 observations of male huddle imagery                                                                                                                                                                                                                                                                                        | <br /> |
| n\_single             | how many of the 55 colonies had a single observation of male huddle imagery                                                                                                                                                                                                                                                                                       | <br /> |
| total\_count\_mean    | total count of all mean of 'male huddle' individual counts                                                                                                                                                                                                                                                                                                        | <br /> |
| coeff\_se\_systematic | total uncertainty derived from the windchill model weather coefficients (reported by Winterl et al. 2024). This is treated as systematic error source, applying the same error to all colonies. Calculated by summing the coeff\_se from all colonies, as the coefficient errors are correlated across colonies and will act in the same direction at all sites.  | <br /> |
| obs\_se\_random       | total uncertainty derived from the observation error, from the variation is SAR observations at each colony when multiple male huddle images were available. This is treated as a random error source as each obs error is independent between colonies. Calculated by combining obs\_se in quadrature across all colonies to account for this.                   | <br /> |
| combined\_se          | total combined standard error for the global breeding estimate, representing the best estimate of total uncertainity in accounting for the two different sources of error. Calculated by summing the systematic coefficient uncertainity directly and combining it with random obseration uncertainity to quadrature. | <br /> |
| combined\_se\_pct     | combined standard error expressed as percentage of total\_count\_mean                                                                                                                                                                                                                                                                                             | <br /> |

<br />

#### File: SAR_datav2_ERA5_v7_cleaned.csv *and*

#### File: sar_huddles_20250502_ERA5_v3_grouped_era5added.csv

**Description:**  The two datafiles that contain the image covariates and the extracted ERA5 weather reanalysis data, prior to the density analysis being undertaken. sar_huddles...xxyy contains data from LaRue et al. 2026 (the six sites that were sampled in 2024) This file contains an additional column (b_pres) which indicates if birds were visible in the image. SAR_datav2_xxyy contains the full dataset from 2025 with all images that captured emperor penguin huddles. Images that did not capture birds were excluded from this dataset. This file contains an additional column (group) which was used for organising the imagery into separate ArcGIS projects. 

####

| Variables        | Definition                                                                                                                 | <br /> | <br /> |
| :--------------- | :------------------------------------------------------------------------------------------------------------------------- | :----- | :----- |
| colony\_name     | colony name                                                                                                                | <br /> | <br /> |
| site\_id         | four letter code for colony name                                                                                           | <br /> | <br /> |
| group            | group colony is in for arcmap projects                                                                                     | <br /> | <br /> |
| image\_id        | image ID provided by umbra, only including images that were in the right location and could have had birds visible in them | <br /> | <br /> |
| date             | date image captured                                                                                                        | <br /> | <br /> |
| month            | month image captured                                                                                                       | <br /> | <br /> |
| day              | day image captured                                                                                                         | <br /> | <br /> |
| year             | year image captured                                                                                                        | <br /> | <br /> |
| DOY              | day of year image captures (calculated from date, jan 1st = 1, dec 31st = 365)                                             | <br /> | <br /> |
| lat              | latitude of image task                                                                                                     | <br /> | <br /> |
| lon              | longitude of image task                                                                                                    | <br /> | <br /> |
| avg\_size        | average size of colony based on LaRue et al. 2024 (if discovered by then) or Fretwell et al. 2024 or Wienecke et al. 2024  | <br /> | <br /> |
| area\_m2         | huddle area in m2                                                                                                          | <br /> | <br /> |
| observation(1-5) | ease of observation metric                                                                                                 | <br /> | <br /> |
| grazing          | grazing angle of image task                                                                                                | <br /> | <br /> |
| incidence        | incidence angle of image task                                                                                              | <br /> | <br /> |
| azimuth          | azimuth angle of image task, difference between satellite position and North (0degrees)                                    | <br /> | <br /> |
| resolution       | resolution of image task (0.25m-1m)                                                                                        | <br /> | <br /> |
| looks            | whether image was multilooked or single looked (1 or 2 looks)                                                              | <br /> | <br /> |
| orbit\_state     | whether satellite was ascending or descending                                                                              | <br /> | <br /> |
| polarization     | polarization of image task (VV or HH)                                                                                      | <br /> | <br /> |
| slant\_range     | distance in metres (slant\_range) between satellite and target                                                             | <br /> | <br /> |
| surface\_type    | surface type that birds were located on (fast ice, multi-year ice, ice berg, ice shelf,  rock, glacier)                    | <br /> | <br /> |
| obs              | observation EOO value shortened                                                                                            | <br /> | <br /> |
| date\_time       | date time extracted from image id                                                                                          | <br /> | <br /> |
| time             | time extracted from image id                                                                                               | <br /> | <br /> |
| time\_UTC        | time in UTC                                                                                                                | <br /> | <br /> |
| date\_UTC        | date in UTC                                                                                                                | <br /> | <br /> |
| ts               | formatted date time                                                                                                        | <br /> | <br /> |
| met\_ff10        | wind speed clculated from u and v wind components, at 10m above surface using lat long and timestamp, era5 extracted       | <br /> | <br /> |
| temp\_airK       | temperature in Kelvin, at 2m above surface at lat lon and time, era5 extracted                                             | <br /> | <br /> |
| met\_humc        | humidity, calculated from surface pressure, temperature and dew point                                                      | <br /> | <br /> |
| met\_rad         | solar radiation at surface, as our observations occur in winter, most are  0                                               | <br /> | <br /> |
| d2m              | dew point at 2m above surface, used to calculate humidity                                                                  | <br /> | <br /> |
| rh\_water        | relative humidity in relation to water, if temperature is above 0 the relative humidity column uses this value             | <br /> | <br /> |
| rh\_ice          | relative humidity in relation to ice, if temperature is below 0 the relative humidity column uses this value               | <br /> | <br /> |

## Code/software

SAR imagery was analysed in ArcGIS Pro (v. 3.4.0), through which we delineated huddle areas and extracted data for density modelling. 

All other analyses were conducted using Python (v. 3.14.3). We used freely available packages *pandas* [v. 3.0.1], *NumPy* [v. 2.4.3], *Matplotlib* [v. 3.10.8], and *SciPy* [v.1.17.1].

We have uploaded the different Jupytr notebook codes for each step of the analysis: 

##### **ProcessERA5_Final.ipynb**

**Description:** This code was used to extract ERA5 weather reanalysis data for the density analysis, using the timestamp and location of each image. 

This script has already been run for all the uploaded datasets and does not need to be rerun to recreate our analysis. 

<br />

##### density_model_refined.ipynb

**Description:** This code was used to estimate the density of the birds in each image based on the ERA5 weather reanalysis data and the Winterl et al. (2024) density model. 

This script uses the **SAR_datav2_ERA5_v7_cleaned.csv** and **sar_huddles_20250502_ERA5_v3_grouped_era5added.csv** datasets and produces the **dfRFD_with_predictions_cleaned_final.csv** and **dfMLR_with_predictions_final.csv&#xA0;**&#x64;atasets. 

<br />

##### manual_phenology_BP.ipynb

**Description:** This code was used to derived the breeding pairs from each image that was identified as having only the males in it, or during the 'male huddle' phase. 

This script uses the **dfRFD_with_predictions_cleaned_final.csv** and **dfMLR_with_predictions_final.csv** dataset and produces the **dfHuddle_export_combined_uncertainty.csv** and **dfHuddleMLR_export_combined_uncertainty.csv**  datasets. It also produces the **total_population_summary.csv** dataset. 

<br />

##### chick_comparison_refined.ipynb

**Description:** This code was used perform model validation, comparing our breeding pairs estimates to the number of chicks counted in spring at seven sites. We used additional 2024 data (huddles published in LaRue et al. 2026) for this comparison to assess how our model performed. 

This script uses the **EP_Chick_counts.xlsx**, **dfHuddle_export_combined_uncertainty.csv** and **dfHuddleMLR_export_combined_uncertainty.csv**  datasets to compare the chick counts to our SAR-derived breeding pair estimates. 

<br />

##### compare_size_refined.ipynb

**Description:** This code was used compare our estimated number of breeding adults at each site to the previously estimated sizes of the colonies based on springtime imagery. 

This script uses the **est_size_AllColonies.csv** and **dfHuddle_export_combined_uncertainty.csv** datasets to compare our SAR-derived breeding adult estimates (2 x breeding pairs) to assess how this new methods changes our understanding of the sizes of the colonies around Antarctica. 

#####

## Access information

Other publicly accessible locations of the data:

* [https://github.com/rosetazetta/SAR_EmperorPenguin](https://github.com/rosetazetta/SAR_EmperorPenguin) 

<br />

Additional huddle data from 2024 was accessed through:

LaRue, M., Price, D., Wiki‐Bennett, S., Lee, C.K., Pan, B.J., McCloud, K., Cruickshank, H., Ponniah, A., Zitterbart, D., Winterl, A. and Le Bohec, C., 2026. Tracking Wintertime Behaviour of Emperor Penguins Using High‐Resolution Synthetic Aperture Radar Imagery. *Remote Sensing in Ecology and Conservation*.

<br />

Density model was adapted from: 

Winterl, A., Richter, S., Houstin, A., Barracho, T., Boureau, M., Cornec, C., Couet, D., Cristofari, R., Eiselt, C., Fabry, B. and Krellenstein, A., 2024. Remote sensing of emperor penguin abundance and breeding success. *Nature Communications*, *15*(1), p.4419.
