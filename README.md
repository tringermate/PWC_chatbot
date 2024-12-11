# PWC_chatbot
PWC job application task

I have created two chatbots in jupyter lab. Both of them are RAG bots, with a database from an article about the Vendée Globe - "Who will win the 2024 Vendée Globe?"
https://www.yachtingworld.com/all-latest-posts/who-will-win-the-2024-vendee-globe-155320

  - pwc_contextualize.ipynb
      - A chatbot with two models. The first one rewrites the question to make it a standalone one.
        
  - pwc_without_context.ipynb
      - A simple chatbot that answers questions based on its knowledge

## Intorduction

For both cases I chose a small, open source llms (both FLAN-T5-large and Intel's Dynamic TinyBERT are under 1B parameters), since I am running my codes on a CPU.
I am using LangChain, as it is one of the most popular frameworks for building chatbots - it is simple to use, and efficient.
In the pwc_contextualize.ipynb I have implemented an extra step in the chain: after the user sends a question, a model reformulates it based on the chat history, to make it a standalone question in order to make a more relevant retrieval - and therefore generate a better answer.
I am using FAISS for efficient similarity search.

## Bottlenecks

-The chatbots do not perform as well as intended, which (in my opinion) is largely due to llms' limitations. I believe that with larger models these systems (especially the pwc_contextualize.ipynb) could provide much better answers. 

-I also think, that with better composed prompts the models could generate more accurate answers.

-There are also inefficients in the framework itself, for example the program does not save the database it creates after scraping the website.

-Chunk sizes and overlaps could also be better tailored to the data, and the llms' capabilities.

-The memory handling could also be improved, for example instead of using a buffer window memory, a summarizer model, or even a knowledge graph type memory could be implemented

## Testing

The bots are capable of understanding and answering very basic questions (like "who is the captain of Malizia-SeaExplorer?", or "is it the 11st edition of Vendée?"), however they fail with more complex ones ("Who are the top contenders?"). 



