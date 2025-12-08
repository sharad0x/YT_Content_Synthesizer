# 🎬 YouTube Content Synthesizer  
*A RAG-based Streamlit App Powered by Gemini AI*

This project is a **Retrieval-Augmented Generation (RAG)** application built with **Streamlit**, **LangChain**, **Gemini API**, and **ChromaDB**.  
It extracts transcripts from YouTube videos, processes them into embeddings, and enables:

1. **Chat with Video** – Ask questions about the video and get context-aware answers.  
2. **Notes for You** – Generate structured notes from the video's content.

If the video transcript is not in English, the app automatically **translates it using Gemini** before processing.

---

## Features

### **YouTube Transcript Extraction**
- Extracts transcript in any supported language (e.g., `en`, `hi`, `es`, etc.).
- Falls back to translation if needed.

### **RAG Pipeline**
- Uses **RecursiveCharacterTextSplitter** for chunking.
- Embeddings generated via **sentence-transformers/all-mpnet-base-v2** (local, fast, zero cost).
- Vector storage handled by **ChromaDB**.
- Gemini provides LLM responses for summarization, note-taking, and Q&A.

### **Gemini-Powered Translation & Generation**
- Converts non-English transcripts into English for consistent processing.
- Generates:
  - Important topics  
  - Clean, structured notes  
  - Chat-style answers based entirely on video content  

### **Streamlit Frontend**
- Simple UI with sidebar inputs:
  - YouTube URL  
  - Language code (e.g., `en`, `hi`)  
  - Mode selection: Chat / Notes  

---

## Tech Stack

| Component | Library / Model |
|----------|------------------|
| UI | Streamlit |
| LLM | Google Gemini API |
| RAG Framework | LangChain |
| Text Splitting | langchain-text-splitters |
| Embedding Model | `sentence-transformers/all-mpnet-base-v2` |
| Vector Store | ChromaDB |
| Transcripts | youtube-transcript-api |
| Environment Management | python-dotenv |

---

## Installation

### 1️. Clone the Repository
```
git clone https://github.com/sharad0x/YT_Content_Synthesizer
cd YT_Content_Synthesizer
```

### 2️. Create a Virtual Environment (Optional, but recommended)
```
python -m venv venv
source venv/bin/activate     # Mac/Linux
venv\Scripts\activate        # Windows
```

### 3. Install Dependencies
```
pip install -r requirements.txt
```

---

## Environment Variables

Create a .env file in the project root:
```
GOOGLE_API_KEY=your_api_key_here
```

---

## Run the App
```
streamlit run app.py
```
Your browser will open with the Streamlit interface.

---

## How It Works (Pipeline Overview)

- Extract Transcript using youtube-transcript-api
- Translate (if needed) to English using Gemini
- Chunk Text using RecursiveCharacterTextSplitter
- Generate Embeddings using sentence-transformers/all-mpnet-base-v2
- Store in Vector DB using Chroma
- Query with RAG using Gemini + LangChain
- Output Notes or Start Chat based on user option

---

## Example Use Cases

- Study notes from tutorials
- Chat with long educational videos
- Extract topics from lectures
- Build summaries for research videos
- Quickly understand technical content

---

## Project Structure
```
YT-RAG/
│── app.py
│── support_functions.py
│── requirements.txt
│── .env.example
│── README.md
```