# Taylor Swift

Since [The Eras Tour](https://www.tstheerastourfilm.com/) has just ended sadly, let's now explore why Taylor Swift is so popular! Is it because of her song-writing skills, or is it because of her ability to constantly evolve, connect with fans on a personal level, and create cultural moments that transcend music?

The [taylor](https://taylor.wjakethompson.com/) R package from W. Jake Thompson is a curated data set of Taylor Swift songs, including lyrics and audio characteristics. 
The data comes from Genius and the Spotify API.

There are three main datasets.

> The first is taylor_album_songs, which includes lyrics and audio features from the Spotify API for all songs on Taylor’s official studio albums. Notably this excludes singles released separately from an album (e.g., Only the Young, Christmas Tree Farm, etc.), and non-Taylor-owned albums that have a Taylor-owned alternative (e.g., Fearless is excluded in favor of Fearless (Taylor’s Version)). 

> You can access Taylor’s entire discography with taylor_all_songs. This includes all of the songs in taylor_album_songs plus EPs, individual singles, and the original versions of albums that have been re-released as Taylor’s Version.

> Finally, there is a small data set, taylor_albums, summarizing Taylor’s album release history.

## The Data

```{r}
# Option 1: tidytuesdayR package 
## install.packages("tidytuesdayR")

tuesdata <- tidytuesdayR::tt_load('2023-10-17')
## OR
tuesdata <- tidytuesdayR::tt_load(2023, week = 42)

taylor_album_songs <- tuesdata$taylor_album_songs
taylor_all_songs <- tuesdata$taylor_all_songs
taylor_albums <- tuesdata$taylor_albums

# Option 2: Read directly from GitHub

taylor_album_songs <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/main/data/2023/2023-10-17/taylor_album_songs.csv')
taylor_all_songs <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/main/data/2023/2023-10-17/taylor_all_songs.csv')
taylor_albums <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/main/data/2023/2023-10-17/taylor_albums.csv')

```

### Data Dictionary

# `taylor_album_songs.csv`

|variable            |class     |description         |
|:-------------------|:---------|:-------------------|
|album_name          |character |Album name         |
|ep                  |logical   |Is it an EP                  |
|album_release       |double    |Album release date       |
|track_number        |integer   |Track number        |
|track_name          |character |Track name          |
|artist              |character |Artists             |
|featuring           |character |Artists featured           |
|bonus_track         |logical   |Is it a bonus track         |
|promotional_release |double    |Date of promotional release |
|single_release      |double    |Date of single release      |
|track_release       |double    |Date of track release       |
|danceability        |double    |Spotify danceability score. A value of 0.0 is least danceable and 1.0 is most danceable.        |
|energy              |double    |Spotify energy score. Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity.        |
|key                 |integer   |The key the track is in.                 |
|loudness            |double    |Spotify loudness score. The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track.        |
|mode                |integer   |Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.               |
|speechiness         |double    |Spotify speechiness score. Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value.          |
|acousticness        |double    |Spotify acousticness score. A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.        |
|instrumentalness    |double    |Spotify instrumentalness score. Predicts whether a track contains no vocals. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.   |
|liveness            |double    |Spotify liveness score. Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.            |
|valence             |double    |Spotify valence score. A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).             |
|tempo               |double    |The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.          |
|time_signature      |integer   |An estimated time signature. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). The time signature ranges from 3 to 7 indicating time signatures of "3/4", to "7/4".     |
|duration_ms         |integer   |The duration of the track in milliseconds.       |
|explicit            |logical   |Does the track have explicit lyrics.           |
|key_name            |character |The key the track is in. Integers map to pitches using standard Pitch Class notation. E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on. If no key was detected, the value is -1.         |
|mode_name           |character |Modality of the track.           |
|key_mode            |character |The key of the track.       |
|lyrics              |list      |Track lyrics. These values are all NA. To get the lyrics in nested tibbles, `install.packages("taylor")` and use the source data.|

# `taylor_all_songs.csv`

|variable            |class     |description         |
|:-------------------|:---------|:-------------------|
|album_name          |character |Album name         |
|ep                  |logical   |Is it an EP                  |
|album_release       |double    |Album release date       |
|track_number        |integer   |Track number        |
|track_name          |character |Track name          |
|artist              |character |Artists             |
|featuring           |character |Artists featured           |
|bonus_track         |logical   |Is it a bonus track         |
|promotional_release |double    |Date of promotional release |
|single_release      |double    |Date of single release      |
|track_release       |double    |Date of track release       |
|danceability        |double    |Spotify danceability score. A value of 0.0 is least danceable and 1.0 is most danceable.        |
|energy              |double    |Spotify energy score. Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity.        |
|key                 |integer   |The key the track is in.                 |
|loudness            |double    |Spotify loudness score. The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track.        |
|mode                |integer   |Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.               |
|speechiness         |double    |Spotify speechiness score. Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value.          |
|acousticness        |double    |Spotify acousticness score. A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.        |
|instrumentalness    |double    |Spotify instrumentalness score. Predicts whether a track contains no vocals. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.   |
|liveness            |double    |Spotify liveness score. Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.            |
|valence             |double    |Spotify valence score. A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).             |
|tempo               |double    |The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.          |
|time_signature      |integer   |An estimated time signature. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). The time signature ranges from 3 to 7 indicating time signatures of "3/4", to "7/4".     |
|duration_ms         |integer   |The duration of the track in milliseconds.       |
|explicit            |logical   |Does the track have explicit lyrics.           |
|key_name            |character |The key the track is in. Integers map to pitches using standard Pitch Class notation. E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on. If no key was detected, the value is -1.         |
|mode_name           |character |Modality of the track.           |
|key_mode            |character |The key of the track.       |
|lyrics              |list      |Track lyrics. These values are all NA. To get the lyrics in nested tibbles, `install.packages("taylor")` and use the source data.|

# `taylor_albums.csv`

|variable         |class     |description      |
|:----------------|:---------|:----------------|
|album_name       |character |Album name      |
|ep               |logical   |Is it an EP       |
|album_release    |double    |Album release date    |
|metacritic_score |integer   |Metacritic score |
|user_score       |double    |User score       |

## The Report

For the report, I have used the software R to create an R Markdown file. Some packages I have used include `readxl`, `readr`, `tidyverse`, `lubridate`, `stringr`, and `dplyr`. Do download these packages if they are not already installed on your laptop by running the following command in your R console:

```R
install.packages(c("readxl", "readr", "tidyverse", "lubridate", "stringr", "dplyr"))
```

These packages are essential for data import, manipulation, and analysis throughout the report. The `tidyverse` package, in particular, provides a comprehensive suite of tools for data wrangling, visualization, and statistical analysis. The `lubridate` package helps with handling date-time data, while `readxl` and `readr` are used for reading data files, such as Excel and CSV formats, respectively. The `stringr` and `dplyr` packages simplify string operations and data transformations. Once these packages are installed, you should be able to run the [Taylor_Swift.Rmd](https://github.com/racxxhel/Taylor-Swift-/blob/main/Taylor_Swift.Rmd) without any issues. You may use the R markdown code and further improve on this project!

For easier viewing, you may also download the raw file from the [Taylor_Swift.html](https://github.com/racxxhel/Taylor-Swift-/blob/main/Taylor_Swift.html) and view the html file online. 

Hope you like the project, thank you! ♡
