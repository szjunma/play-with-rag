# Retrieval Augmented Generation with local llm and embedding models

This repo provides an instruction to try RAG with local llm and embedding models. Without the need of internet connection or access token, your data stays in your computer. 

The device I use is an M1 Macbook Pro with 16GB memory. The inference speed is fine with a 7B model, but a faster machine is recommended. 

## Set up environment

Create a conda environment and build `llama-cpp-python` on METAL to enable GPU support.
```bash
conda create -n rag python=3.9 ipykernel
conda activate rag

CMAKE_ARGS="-DLLAMA_METAL_EMBED_LIBRARY=ON -DLLAMA_METAL=on" pip install -U llama-cpp-python --no-cache-dir
pip install llama-index llama-index-llms-llama-cpp llama-index-embeddings-huggingface
```

## Download llm and embedding models
The llm model I use is [gpt4all-falcon](https://huggingface.co/nomic-ai/gpt4all-falcon). Download the entire folder and place it in the root directory of this repo. Make sure to convert the model itself to gguf format. Alternatively, you can also just download the quantized model [here](https://gpt4all.io/models/gguf/gpt4all-falcon-newbpe-q4_0.gguf) and place it in the folder.

The embedding model is [UAE-Large-V1](https://huggingface.co/WhereIsAI/UAE-Large-V1). Download it to the root directory of this repo.

## Test with your data
Gather some text and place them into `/data`. Now run the notebook with the kernel you just set up. Compare the response with and without RAG. Have fun. 