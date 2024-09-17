# Tutelary: An AI Guide to Consumer Privacy

Tutelary is an conversational chatbot built from an Advanced RAG (Retrieval-Augmented Generation) agent made with Haystack.

Tutelary is designed to assist users in reclaiming their privacy by walking the user through creating a personal threat model, selecting and interpreting potential applications, and installing necessary or alternative software (e.g. VPNs, Browsers, Extensions, etc.). It is not intended to be wholly comprehensive, but it is intended to be resource for those looking to reclaim their personal privacy through the thoroughly vetted recommendations of not-for-profit privacy advocacy group [PrivacyGuides](PrivacyGuides.org).

## Overview

- [Features](#Features)
- [Installation](#Installation)
- [Usage](#Usage)
- [Demo](#Demo)
- [Pipeline Diagrams](#Pipelines)
- [License](#License)

## Features

- Indexes and embeds the PrivacyGuides.org Knowledge Base Markdown files into an Elasticsearch DB
  - Embeds documents using "avsolatorio/GIST-small-Embedding-v0"
- Queries the DB with advanced hybrid keyword and semantic search algorithms
  - Reranks documents using BAAI/bge-reranker-base
- _(Future)_ Hosted on GCP with Next.js frontend

## Installation

1. Clone the repository

```zsh
 git clone https://github.com/vjawarani/tutelary.git
```

2. Set up a Docker container for the Elasticsearch Database on 9200. The current compose.yaml should accomodate for this, so the following command will suffice.

```zsh
 docker compose up --build
```

3. Set your OPENAI_KEY as an env variable that is accessible by [tutelary.ipynb](notebooks/tutelary.ipynb).
```zsh
 export OPENAI_KEY=<key>
 ```

You may also insert your key into the following line in [tutelary.ipynb](notebooks/tutelary.ipynb).
```python
# os.environ["OPENAI_KEY"] = <your key>
```

4. Run [tutelary.ipynb](notebooks/tutelary.ipynb). **It contains the installation of all packages and dependencies, so create a virtual environment if necessary.**

```zsh
jupyter notebook notebooks/tutelary.ipynb
```

## Usage

Just start with a hi. The prompt is designed to handle the rest.

## Demo

![Demo](notebooks/imgs/demo.gif "Demo")

## Pipelines

The pipeline diagrams can be found here:
- [Indexing](notebooks/imgs/indexing.png "Indexing")
- [Retrieval](notebooks/imgs/rag.png "Retrieval")

## License

This project is licensed under the [GNU License](https://www.gnu.org/licenses/gpl-3.0.en.html).
