# Netflix Titles Dataset Analysis

## About the Dataset

Netflix, one of the biggest names in media and video streaming, offers over 8000 films and TV shows to a global audience of 200 million subscribers. This project uses the Netflix Titles dataset, which provides detailed information about the movies and TV shows available on the platform, including details like cast, directors, ratings, release year, duration, and genre.

## Dataset Overview

The dataset contains comprehensive information about Netflix's offerings, including movies and TV shows. It includes key attributes like title, type (movie or TV show), director, cast, country of origin, release year, rating, and a brief description.

### Key Columns:
- `show_id`: A unique identifier for each title.
- `type`: The type of the title (movie or TV show).
- `title`: The name of the movie or TV show.
- `director`: The director(s) of the title.
- `cast`: The list of main actors/actresses.
- `country`: The country or countries where the movie/show was produced.
- `date_added`: The date the title was added to Netflix.
- `release_year`: The year the title was released.
- `rating`: Age classification for the title.
- `duration`: The duration of the movie in minutes, or the number of seasons for TV shows.
- `listed_in`: Genres the title belongs to.
- `description`: A brief summary of the title.

## Key Statistics

- **Total Entries**: 8809 (movies and TV shows)
- **Columns**: 12 columns representing various details of the titles.

## Installation

To run this project, you'll need the following Python libraries:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `plotly`

You can install them using `pip`:

```bash
pip install numpy pandas matplotlib seaborn plotly
```

## Dataset Exploration

1. **Loading the Dataset**:  
The dataset is loaded using pandas `read_csv()` method.

```python
import pandas as pd
data_frame = pd.read_csv("netflix_titles.csv")
```

2. **Checking for Missing Data**:  
A heatmap is used to visualize missing values in the dataset.

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(9, 8))
sns.heatmap(data_frame.isnull())
plt.show()
```

3. **Exploring Data**:  
We explore the leading movie producers (countries) and the distribution of movies vs TV shows in the dataset.

```python
leading_movie_producers = data_frame.country.value_counts().nlargest(20)
```

4. **Distribution of Content**:  
A pie chart is used to compare the counts of movies and TV shows.

```python
plt.pie(data_counts, autopct='%.2f%%', textprops={'fontsize': 14})
```

5. **Yearly Content Distribution**:  
A line chart and bar plots are created to show the distribution of movies and TV shows by release year.

```python
data_frame['release_year'].value_counts().sort_index().plot(kind='line')
```

## Visualizations

- **Top Movie Producers**:  
  A bar chart showing the top 20 countries producing Netflix content.

- **Movies vs TV Shows**:  
  A pie chart comparing the distribution of movies and TV shows on Netflix.

- **Content Distribution Over the Years**:  
  A line chart displaying the yearly count of titles added to Netflix.

- **Director Analysis**:  
  A bar plot showing the most prolific directors in the dataset for movies.

```python
top_directors_by_movie_type = Movie.groupby('director')['type'].value_counts().sort_values(ascending=False).head(15)
```

## Usage

1. **Exploratory Data Analysis (EDA)**:  
   The dataset is analyzed to uncover insights regarding Netflix’s content. Key analysis points include:
   - **Missing Data**: The percentage of missing values for each column is calculated.
   - **Leading Movie Producers**: The top 20 countries producing Netflix content are visualized using a bar plot.
   - **Movie vs TV Show Count**: A pie chart visualizes the proportion of movies and TV shows in the dataset.
   - **Content Distribution by Year**: A line chart and a bar plot are used to show how Netflix's content has evolved year by year.

2. **Director Analysis**:  
   The top directors contributing to the movie category are identified and ranked by their number of films on Netflix.

3. **Content by Year of Release**:  
   A detailed yearly breakdown of content types (movies vs TV shows) is shown, helping to identify trends in content release.

4. **Visualizing Data**:  
   You can use the following functions to generate key visualizations for your analysis:
   
   - **Missing Data Heatmap**: Shows missing data across the dataset.
   - **Content Type Distribution**: Visualizes the distribution of content types (movies vs TV shows).
   - **Top 20 Movie Producers**: Displays the 20 leading countries producing Netflix content.
   - **Content Type by Year**: Tracks the release of movies and TV shows over the years.

```python
# Heatmap to identify missing data
plt.figure(figsize=(9, 8))
sns.heatmap(data_frame.isnull())
plt.show()

# Bar plot for leading movie producers
plt.figure(figsize=(9, 10))  
leading_countries = data_frame.country.value_counts().head(20) 
sns.barplot(x=leading_countries.values, y=leading_countries.index, palette='muted')
plt.show()

# Pie chart for movie vs TV show distribution
plt.figure(figsize=(9, 5))
chosen_colors = plt.cm.Set2.colors  
data_counts = data_frame['type'].value_counts()  
plt.pie(data_counts, autopct='%.2f%%', textprops={'fontsize': 14}, colors=chosen_colors)  
plt.show()
```

## Analysis and Insights

The analysis conducted on the dataset yields several insights:

- **Leading Content Producers**: The dataset highlights the countries that produce the most content for Netflix. The top 20 countries are identified, and the U.S. leads with the highest number of titles.
- **Movies vs TV Shows**: A substantial portion of Netflix’s content consists of movies, but TV shows have gained popularity, with several countries producing more TV shows in recent years.
- **Content Trends Over Time**: There has been a consistent increase in content releases since 2009, particularly after Netflix expanded globally.
- **Director Analysis**: Some directors have contributed significantly to Netflix’s movie catalog, with a few names consistently appearing in the top rankings.

## Contributions

This project is open to contributions! If you want to contribute, please fork the repository, create a new branch, and submit a pull request with your proposed changes.

## How to Run the Project

1. **Clone the Repository**:  
   To get started with the project, clone the repository to your local machine using the following command:

   ```bash
   git clone https://github.com/rishabhdarji/ML-Project.git
   ```

2. **Navigate to the Project Directory**:  
   Change your working directory to the project folder:

   ```bash
   cd netflix-titles-analysis
   ```

3. **Install Dependencies**:  
   If you haven’t already, make sure you have all the required dependencies installed. You can do so by running:

   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Jupyter Notebook**:  
   The project is structured around Jupyter Notebooks for analysis and visualization. To run the notebook, use:

   ```bash
   jupyter notebook
   ```

   This will open the notebook interface in your browser. Open the relevant `.ipynb` file to start exploring the analysis.

## Project Structure

The project is structured as follows:

```
netflix-titles-analysis/
│
├── data/                     # Folder containing the dataset(s)
│   └── netflix_titles.csv     # The Netflix Titles dataset
│
├── notebooks/                 # Jupyter notebooks with analysis and visualizations
│   └── netflix_analysis.ipynb # Main analysis notebook
│
├── requirements.txt          # List of dependencies
├── README.md                 # This README file
```

- **data/**: Contains the dataset used for analysis (`netflix_titles.csv`).
- **notebooks/**: Contains the Jupyter Notebooks where the analysis and visualizations are performed.
- **requirements.txt**: A text file containing the dependencies needed to run the project.
- **README.md**: This file with instructions and details about the project.
- **LICENSE**: The project's license (MIT in this case).

## Testing

While this project is primarily focused on data analysis and visualization, you can add your own tests for various functions. Here’s a simple example of how you might add a test for checking if the dataset loads correctly:

1. **Create a new test file** in the root directory (e.g., `test_dataset.py`).

2. **Use pytest** to write simple tests for the project. Example:

```python
import pandas as pd

def test_dataset_load():
    # Load the dataset
    data = pd.read_csv('data/netflix_titles.csv')

    # Check if the dataset contains the expected number of rows
    assert len(data) == 8809, "Dataset should contain 8809 entries"

def test_column_names():
    # Load the dataset
    data = pd.read_csv('data/netflix_titles.csv')

    # Check if specific columns exist
    required_columns = ['show_id', 'type', 'title', 'director', 'cast', 'country', 'date_added', 'release_year', 'rating', 'duration', 'listed_in', 'description']
    for column in required_columns:
        assert column in data.columns, f"Column '{column}' is missing from the dataset"
```

3. **Run the tests**:

```bash
pytest test_dataset.py
```

## Conclusion

This analysis provides insights into the distribution of content on Netflix, the impact of movie producers, and the trends in movie and TV show releases over time. The dataset helps to understand the evolution of Netflix's content library, both in terms of quantity and diversity.
