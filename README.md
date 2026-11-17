# Day 8: Text Preprocessing Pipeline in Python (NLTK & Regex)

Part of the **60 Days AI Engineering Challenge** — building a complete NLP text preprocessing workflow from scratch to convert messy, real-world text into clean, machine-readable tokens.

---

## 📌 Overview
Raw human language contains noise such as punctuation, emojis, inconsistent casing, and high-frequency filler words (stopwords) that reduce NLP model efficiency and inflate vocabulary size. This project implements an end-to-end preprocessing pipeline across three distinct real-world text domains:
1. **Social Media Post** (emojis, hashtags, mentions, exclamations)
2. **News Article** (formal punctuation, mixed casing, multi-clause sentences)
3. **Customer Review** (slang, contractions, emojis, uppercase emphasis)

---

## 🛠️ Tech Stack & Libraries
- **Python 3**
- **NLTK (Natural Language Toolkit):** `sent_tokenize`, `word_tokenize`, `stopwords`, `PorterStemmer`, `WordNetLemmatizer`
- **Regex (`re`):** Pattern-based noise and punctuation removal

---

## ⚙️ Preprocessing Pipeline Steps

1. **Sentence-Level Tokenization (`sent_tokenize`)**  
   Splits continuous paragraphs into individual sentences to preserve sentence boundaries.
2. **Word-Level Tokenization (`word_tokenize`)**  
   Breaks sentences down into discrete word and symbol tokens.
3. **Lowercasing & Punctuation/Emoji Stripping (`re.sub`)**  
   Normalizes casing and removes non-alphanumeric characters so tokens like `"AI"`, `"ai"`, and `"AI!!"` map to the same representation.
4. **Stopword Removal (`stopwords.words('english')`)**  
   Filters out common filler words (`the`, `is`, `and`, `at`) and compares unique vocabulary size before and after removal.
5. **Stemming vs. Lemmatization**  
   - **`PorterStemmer`**: Fast rule-based suffix stripping (e.g., `regulating` → `regul`, `battery` → `batteri`).
   - **`WordNetLemmatizer`**: Context-aware dictionary root extraction (e.g., `regulating` → `regulate`, `battery` → `battery`).

---

## 🧠 Why Each Step Matters (And What Breaks If Skipped)

| Step | Purpose | What Breaks If Skipped |
| :--- | :--- | :--- |
| **Tokenization** | Segments raw strings into structured units | Models cannot index words or detect sentence boundaries. |
| **Case & Punctuation Normalization** | Merges duplicate token variations | Vocabulary size explodes with redundant tokens (`fast` vs `fast!`). |
| **Stopword Removal** | Removes low-information filler words | Bag-of-Words / TF-IDF models get dominated by noise instead of key signals. |
| **Stemming / Lemmatization** | Reduces inflected words to base forms | Models treat different tenses/plurals (`runs`, `running`, `ran`) as unrelated words. |

---

## 🚀 How to Run

1. Clone this repository or open `Day_8_Text_Preprocessing.ipynb` in **Google Colab** / **Jupyter Notebook**.
2. Install NLTK (if running locally):
   ```bash
   pip install nltk
