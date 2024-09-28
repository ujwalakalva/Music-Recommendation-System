Music Recommendation System
This is a simple Song Recommendation System that uses TF-IDF (Term Frequency-Inverse Document Frequency) and Cosine Similarity to recommend songs based on text (lyrics) similarity.

Project Structure
songdata.csv: This dataset contains information about songs, artists, and lyrics. The dataset has the following columns:

artist: Name of the artist.
song: Name of the song.
link: A link to the song's webpage (this column is removed for simplicity).
text: Lyrics of the song.
similarity.pkl: A pickle file that contains the precomputed cosine similarity matrix of the song lyrics. This is used for making recommendations without recalculating the similarity each time.

df.pkl: A pickle file that stores the processed dataset after cleaning and sampling, which is used for recommendations.

Data Preprocessing
Cleaning: The dataset was sampled to 5000 records for faster processing. The text column (lyrics) was converted to lowercase, and all non-alphabetical characters and newlines were removed.

Tokenization & Stemming: The song lyrics were tokenized using NLTK's word_tokenize function, and each token was stemmed using the Porter Stemmer.

TF-IDF Matrix: The lyrics were transformed into a TF-IDF matrix using TfidfVectorizer with the English stop words removed. This matrix is used to compute cosine similarity between songs.

Cosine Similarity: Using the TF-IDF matrix, cosine similarity was computed between all songs, which measures how similar two songs are based on their lyrics.

Functions
tokenization(txt):

Tokenizes the input text and applies stemming to each token.
Returns the processed text.
recommendation(song_df):

Recommends 20 songs that are most similar to the given song based on cosine similarity.
Input: song_df (name of the song for which you want recommendations).
Output: List of 20 recommended songs.
How to Use
Load the precomputed data:
import pickle
df = pickle.load(open('df.pkl', 'rb'))
similarity = pickle.load(open('similarity.pkl', 'rb'))
Get song recommendations:
recommendations = recommendation('Alma Mater')
print(recommendations)
Requirements

Make sure you have the following libraries installed:
pandas
numpy
nltk
scikit-learn
pickle
You can install the dependencies using:

bash
Copy code
pip install pandas numpy nltk scikit-learn
Example Usage
To recommend songs similar to "Alma Mater", the following code can be used:

recommendation('Alma Mater')
This will return a list of 20 songs that are lyrically similar to "Alma Mater".
