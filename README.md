# Taylor Swift analysis project

This project analyzes Taylor Swift's discography, aiming to provide insights into the aspects of her albums and songs that make her music so attractive to listeners. It includes an analysis of Spotify parameters to explore elements such as danceability and speechiness across her albums. The dataset used for this analysis can be found at this [link](https://www.kaggle.com/datasets/delfinaoliva/taylor-swift-discography).

## Table of contents
* [Introduction](#-introduccion)
* [Data](#data)
* [Methodology](#methodology)
* [Results and conclusion](#results-and-conclusion)
* [Final note](#final-note)

## Introduction

This is my first data analysis project using Python. I chose this topic because I'm a fan of Taylor Swift's music, and exploring her work beyond her lyrics and personal history seemed fascinating to me. As one of the greatest songwriters of this century, Taylor Swift's music offers many interesting aspects to analyze.

This project covers relationships between various factors such as Spotify streams, the number of songs that reached Spotify's global top charts, album physical sales, and characteristics of her songs like track themes, danceability, acousticness, energy, instrumentalness, liveness, loudness, speechiness, tempo, and valence.

Additionally, I provide insights into her albums, focusing on her original studio albums and their re-recordings.

Finally, I included a section where I analyzed "The Top Songs", highlighting the most streamed tracks and the longest songs in her discography.

## Data

The dataset for my analysis can be found at this [link](https://www.kaggle.com/datasets/delfinaoliva/taylor-swift-discography).

The columns in this dataset are:
* ID - unique identifier for each track
* track_name - the name of the track
* track_musical_genre - the genre classification of the track
* track_type - the type of track, which could indicate if it’s a single, remix, or b-side
* duration_ms - the duration of the track in milliseconds
* feature - whether the track features other artists
* track_videoclip - indicates if the track has an official videoclip
* videoclip_views - the number of views of the track's videoclip on YouTube
* spotify_streams - the number of streams the track has on Spotify
* spotify_global_peak - the highest global ranking the track achieved on Spotify charts
* album - the name of the album
* track_number - the order the song appears on his album
* album_musical_genre - the genre of the album
* album_type - the type of album (e.g., studio, compilation, deluxe)
* release_date - the release date of the album
* album_physical_sales - the physical sales of the album
* track_lyrics - the lyrics of the track
* track_theme - the main theme or subject matter of the track
* uri - the Spotify URI for the track
* acousticness - a measure of how acoustic the track is (0 to 1)
* danceability - a measure of how suitable the track is for dancing (0 to 1) based on a combination of musical elements including rhythm stability, tempo and beat
* energy - the intensity and activity level of the track (0 to 1). Typically, energetic tracks feel fast, loud, and noisy
* instrumentalness - a measure of how much of the track is instrumental (0 to 1). The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content
* liveness - a measure of how "live" the track feels, indicating audience presence (0 to 1). Tracks with higher liveness values are more likely to have been performed in a live setting
* loudness - the overall loudness of the track in decibels (dB). Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typically range between -60 and 0 db
* speechiness - a measure of the amount of spoken words in the track (0 to 1). The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value
* tempo - the tempo or speed of the track in beats per minute (BPM). Tempo is the speed or pace of a given piece and derives directly from the average beat duration
* valence - a measure of how positive or negative the track sounds (0 to 1). Tracks with high valence sound more positive

Before starting the analysis, I performed several preprocessing steps to obtain clean data. These steps included:

* Handling missing values: I identified 2 missing values in the column 'album_physical_sales.' The corresponding songs were from an album that was not for sale, as it is a Spotify playlist of the surprise songs performed during the 'Reputation Stadium Tour.' Therefore, I consider the sales for these songs to be 0, consistent with the other songs from that album.

* Handling data types: I found some columns that needed to have their data types changed. These columns included:
  * instrumentalness: from object to float
  * videoclip_views: from object to integer
  * spotify_streams: from object to integer
  * release_date: from object to datetime
  * album_physical_sales: from object to integer

* Handling error in data: I discovered that the column 'album_physical_sales' had issues with two albums: 'Speak Now' and 'Midnights (The Til Dawn Edition).' Each album had two possible values for sales, so I decided to check the number of songs in each album that had different sales figures. I found that the least number of songs for each case matched the sales value of other albums with similar names ('Speak Now (Deluxe Edition)' and 'Midnights (3am Edition)'). Therefore, I assumed this discrepancy was a mistake and assigned the other value to all the songs in the first two albums.

Then, I performed some processing to simplify the data for analysis. This included:
* Creating a new column called 'duration_min': This column was created from the 'duration_ms' column, which contained the duration of each song in milliseconds. I decided it would be easier to read this information in minutes, as it is more common to discuss song durations in that format.
* Create a new dataframe with album information only: it was easier to have information in a different table called df_albums to perform the analysis of the albums. The columns of this dataframe are:
  * album: name of the album
  * album_physical_sales: the physical sales of the album
  * album_musical_genre: the musical genre of the album
  * album_type: the type of album (e.g., studio, compilation, deluxe)
  * release_date: release date of the album
  * number_of_tracks: total number of tracks in the album
  * duration_min: total duration of the album in minutes

## Methodology

The visualization tools used in this project were:
* Matplotlib
* Seaborn
* Plotly

And the library used for data manipulation was Pandas.

## Results and conclusion



### General Analysis

In this section, I addressed some general questions about the data, such as:

* How many tracks are there per album?
* How many physical copies of each album were sold?
* Is there a relationship between the number of tracks on an album and its physical sales?
* Which genres are most commonly used by Taylor Swift?
* Which are her most streamed albums?
* How is the distribution of song durations across her discography?
* How many tracks from each album reached Spotify's Global Top 50 chart?
* Is there a relationship between track number and Spotify streams for each song?
* Is there a relationship between song length and Spotify streams?

Some key findings from this analysis are:

* The most common genres used by Taylor Swift are country pop, pop rock, synth pop, and indie folk.
* Her songs have an average duration of around 4 minutes.
* The first tracks of an album tend to be more streamed than the later ones.

### Analysis of Original Studio and Re-recorded Albums
I then focused on comparing her original studio albums with her re-recorded albums. Since 2021, Taylor Swift has been re-recording her albums to regain ownership of the copyright in her master recordings, as she was not given the opportunity to purchase them from her former management company. I thought it would be interesting to explore the data in these cases.

In this section, I answered the following questions:

* Which album genres are the best-selling?
* How many copies of each album type were sold?
* How many physical albums were sold over the years of release?
* How many tracks have her albums had over time?
* What was the duration of her albums over time?
* Is there a relationship between album length (duration) and physical sales?
* What is the distribution of album durations?

Key findings from this section include:

* Sales of her re-recordings represent about 50% of the sales of all her original studio albums (with her first original album released in 2006, and the first re-recording in 2021).
* The best-selling album is 1989, which was her first pop album. Lower sales are seen in evermore, Fearless (Taylor's Version), and Red (Taylor's Version), likely due to the pandemic.
* There was an increase in Spotify streams with Lover, her first fully-owned studio album after her previous studio albums were sold by her former management company.

### Analysis of Spotify Parameters

Next, I analyzed several Spotify parameters by album, including:

* Track theme
* Acousticness
* Danceability
* Energy
* Instrumentalness
* Liveness
* Loudness
* Speechiness
* Tempo
* Valence

Key findings from this section are:

* The top 3 track themes are 'Falling in Love', 'Broken Heart/Sadness', and 'New Love'.
* folklore: the long pond studio sessions has the highest acousticness, likely due to it being an acoustic session.
* reputation is the album with the highest danceability, which makes sense given its style.
* reputation Stadium Tour Surprise Songs Playlist is the most energetic album, probably because it's recorded live on tour, and also because it's her longest album.

### Top 10s

Finally, I analyzed some metrics on her top songs:

* Top 10 most streamed songs
* Top 10 most streamed songs with a feature
* Top 10 most streamed songs with a music video
* Top 10 longest songs

Key findings from this section include:

* 'Cruel Summer' is the most streamed song.
* 'I Don't Wanna Live Forever' is the most streamed song with a feature, and was part of the Fifty Shades Darker movie soundtrack.
* Her longest song is 'All Too Well (10 Minute Version) (Taylor's Version) (From the Vault)', which is 10 minutes and 13 seconds long.
* Her most streamed song with a music video is 'Blank Space'.

### Final Note
I would like to clarify that this data covers up to 2023. However, a new album was released in 2024. By the end of this analysis, I noticed that an updated version of the dataset, which includes her latest album, is available. I plan to analyze this updated data in the near future.






