# 📚 BookChat – Chat with Any Public Domain Book

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/BookChat/blob/main/bookchat.ipynb)

**BookChat** is a fully local RAG (Retrieval-Augmented Generation) system that lets you **chat with any public domain book** from Project Gutenberg – all running inside a free Google Colab notebook.  
No API keys, no cloud costs, and your data never leaves the environment.

---

## ✨ Features

- 🔍 **Retrieval-Augmented Generation** – find exact passages and generate answers grounded in the book.
- 📖 **Any Project Gutenberg book** – just enter the book ID (e.g., `84` for *Frankenstein*, `1342` for *Pride and Prejudice*).
- 🧠 **Local LLM** – uses `microsoft/phi-2` (2.7B) in 4‑bit quantization – fits in Colab’s free tier.
- ⚡ **Fast vector search** – FAISS index + `all-MiniLM-L6-v2` embeddings.
- 💾 **Persistent storage** – save index and chunks to Google Drive for reuse.
- 🖥️ **Interactive chat UI** – powered by Gradio, with source citations.
- 🔒 **Privacy first** – everything runs locally; no external API calls.

---

## 🚀 How to Use

1. **Click the “Open In Colab” badge** above – the notebook will open in Google Colab.
2. **Run all cells** (Runtime → Run all).
3. **Enter a Project Gutenberg book ID** when prompted (e.g., `84` for *Frankenstein*).
4. **Wait** for the Gradio link to appear (the last cell will output a public URL).
5. **Ask anything** about the book in the chat interface.

> 💡 **Tip:** If you run out of memory, switch to the smaller `TinyLlama` model (see comments in Cell 6).

---

## 📋 Requirements (all installed automatically in Colab)

- `sentence-transformers`
- `faiss-cpu`
- `transformers` + `accelerate` + `bitsandbytes`
- `gradio`
- `langchain-text-splitters`
- `pypdf`

---

## 🧪 Example Interaction

**Book:** *Frankenstein* by Mary Shelley (ID `84`)

> **User:** Who is the main character?  
> **BookChat:** Victor Frankenstein is the main character, a scientist who creates a living creature.  
> **Sources:** *Chapter 1: “I am by birth a Genevese; my family is one of the most distinguished of that republic…”*

---

## 🗂️ Project Structure
```
BookChat/
├── bookchat.ipynb 
└── README.md 
```

---

## 🛠️ How It Works (Inside the Notebook)

| Cell | Step |
|------|------|
| 1 | Install dependencies |
| 2 | Download book from Project Gutenberg |
| 3 | Split into overlapping chunks (512 tokens, 80 overlap) |
| 4 | Generate embeddings and build FAISS index |
| 5 | Save index and chunks as JSON (safe, no pickle) |
| 6 | Load `phi-2` LLM in 4‑bit quantization |
| 7 | Define retrieval and generation functions |
| 8 | Launch Gradio chat interface |
| 9 | Quick evaluation with auto‑generated questions |
| 10 | (Optional) Save everything to Google Drive |

---

## 📦 Saving & Reloading Your Index

After running Cell 10, your index and chunks are saved to Google Drive.  
To reuse them in a future Colab session:

1. Mount your Drive.
2. Load the JSON chunks and FAISS index as shown in the commented code at the end of Cell 10.

This avoids re‑embedding the entire book.

---

## 🤝 Contributing

Pull requests are welcome! Ideas for improvement:
- Add support for PDF uploads (local files)
- Implement conversational memory
- Add hybrid search (BM25 + vector)
- Support more languages (multilingual embeddings)

---

## 📄 License

MIT – feel free to use, modify, and share.

---

## 🙏 Acknowledgements

- [Project Gutenberg](https://www.gutenberg.org/) for the free eBooks
- [Hugging Face](https://huggingface.co/) for transformers & sentence-transformers
- [Google Colab](https://colab.research.google.com/) for free GPU resources

---

**⭐ Star this repo if you found it useful – and happy reading!**  
