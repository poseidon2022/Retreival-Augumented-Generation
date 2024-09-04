# Retrieval-Augmented Generation (RAG) Project

## Overview
This project implements Retrieval-Augmented Generation (RAG), a technique designed to enhance the responses of large language models (LLMs) by integrating external knowledge. By leveraging Google Generative AI for document embedding and Pinecone for vector storage and retrieval, the system provides contextually accurate and relevant answers to user queries.

## Key Features
- **Document Embedding**: Converts documents into vector embeddings using Google Generative AI, enabling efficient context retrieval.
- **Vector Storage**: Manages and stores vector embeddings in Pinecone, a vector database that supports scalable and fast retrieval.
- **Contextual Augmentation**: Enriches queries with relevant context retrieved from the vector store, improving response quality.
- **Generative Response**: Uses an LLM to generate responses based on the augmented query context, offering precise and contextually relevant answers.

## Installation
To set up the project, install the required dependencies:

```bash
pip install --upgrade fsspec==2024.6.1
pip install -qU \
  langchain==0.0.300 \
  datasets==2.14.6 \
  pinecone-client==2.2.4 \
  tiktoken==0.5.1
pip install langchain_google_genai
pip install pypdf==3.1.0
```
## Setup

### Google Generative AI
Initialize the Google Generative AI client with your Google API key. This client will be used for generating embeddings and responses.

### Pinecone
Set up Pinecone for vector storage and retrieval. Ensure you have your Pinecone API key and specify the environment configuration.

## Usage

### Document Loading and Chunking
1. **Load Document**: Use `PyPDFLoader` to load PDF documents.
2. **Split Document**: Apply `RecursiveCharacterTextSplitter` to divide the text into smaller chunks for embedding.

### Embedding and Storage
1. **Generate Embeddings**: Convert text chunks into embeddings using `GoogleGenerativeAIEmbeddings`.
2. **Store Vectors**: Upsert the generated embeddings into Pinecone. This step involves creating an index in Pinecone and storing the vector data.

### Query Augmentation
1. **Augment Queries**: Enhance user queries with relevant context retrieved from Pinecone to improve the quality of responses.
2. **Generate Responses**: Use the LLM to generate responses based on the augmented query context.

## Example Usage
1. **Initialize Google Generative AI Client**: Set up the client with the required model and API key.
2. **Document Processing**: Load documents, generate embeddings, and store them in Pinecone.
3. **Query Handling**: Augment queries with context and generate responses using the LLM.
