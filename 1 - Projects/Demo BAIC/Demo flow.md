---
id: Demo flow
aliases: []
tags: []
---

<!--toc:start-->

- [Explain and Demo flow BAIC](#explain-and-demo-flow-baic)
  - [Data layer](#data-layer)
    - [Connectors](#connectors)
    - [Data ingestion](#data-ingestion)
  - [Knowledge layer](#knowledge-layer)
  - [Model layer](#model-layer)
  - [Agentic layer](#agentic-layer)
- [Flow Standalone X-Stream](#flow-standalone-x-stream)
<!--toc:end-->

[ ] - enable quartz [Render and deploy the Knowledge base](https://quartz.jzhao.xyz/)

## Explain and Demo flow BAIC

### Data layer

The data layer is composed into various functions that allow us to

#### Connectors

There are two connector types, sources and destinations.
Sources are where we get metadata and data from while destinations (in the UI knowledge base - which I feel is the wrong naming) is where we put the extracted and transformed data into, mainly vector and graph databases.

Allow accessing a wide variety of data sources - conversational - unstructured / documents - enterprise applications (SFDC, Service Now, Dynamics,...) - structured / relational data (snowflake, databricks, MongoDB, postgres, )

_How to demo_

- Open the menu Manage Connectors
- Start with Sources and explain the different kind of sources we can connect to.
- Highlight that Uniphore has been rooted in Conversational AI and our capabilities in real time conversation analysis as well as post call analysis. Open "Add Documents Source" and show how to add an Amazon S3 storage or Confluence. Explain that those and others contain unstructured data including images, tables and graphs that contain detailed knowledge of the business.
- Just go until the detail configuration screen, explain that each connector has its own configuration settings and cancel from there.
- Show quick examples of the Enterprise Applications and Relational Databases and mention Snowflake (with which we have a strong partnership, and they are even invested in Uniphore) and Databriks

---

- Next explain the "Knowledge Base" which is the destination of where the ready to use data will be stored. **_We are not storing / duplicating the original data, only the AI relevant information_**
- [ ] Our default Vector Database is Astra from Datastax and Graph DB is Neo4j #ask but each customer can also bring their own, maybe already existing, Vector DB.
- Explain that we can connect to any Vector DB, or Graph DB, and we support over 25+ #ask Connectors
- From here we transition to the ingestion workflows, now that we have source and destination configured, we need to do the heavy lifting of preparing the data for AI

**_ Useful links _**

- [Vector DB -> Short Explainer Video](https://www.youtube.com/watch?v=klTvEwg3oJ4)
- [Vector DB -> More details](https://www.youtube.com/watch?v=dN0lsF2cvm4)
- [Graph DB -> Short Explainer Video](https://www.youtube.com/watch?v=T6L9EoBy8Zk)
- [Graph DB -> More details](https://www.youtube.com/watch?v=dGHSKpx4Xjs)
- [Graph RAG -> Short Explainer](https://www.youtube.com/watch?v=Aw7iQjKAX2k)
- [Knowledge Graph](https://www.youtube.com/watch?v=O-T_6KOXML4)

#### Data ingestion

Ingestion is different for every connector, but all have something in common. When we ingest data, we are executing a so-called workflow / pipeline, which contains multiple steps that are specific to the source data.

_For each source Uniphore provide a predefined and configured (this are best practise default configurations that can be changed by the user) workflow which will read the source, transform it in different ways and store the AI ready data into our destination sources_

_How to demo_

- Speak about the workflows to read, transform and store the ai ready data.
- Open the "Rapid experimentation" section and demo pick either claims or Network
  - _Have the corresponding documents pre-opened_
  - They can be found [here](https://uniphore.sharepoint.com/:f:/r/sites/GlobalSalesEngineering/Shared%20Documents/Demo%20and%20data/Demo%20Data?csf=1&web=1&e=B6HQoa)
- Explain the complexity of the documents, e.g. Networking show the diagrams / images. For claims, open the complex forms that contain handwritten text and the complex tables in the final report
- Upload the documents and explain that they are now being processed as an experimental flow which the user can change to optimize the outcome. I typically upload the test report, the physicians statement and the final report
- show few documents with the combobox so the UI shows the documents it will process
- start the processing and explain the different updates of the extraction pipeline / workflow on the right side
  - Partitioner [[Partition]]
    The partitioner is responsible for splitting the documents into smaller chunks, which are then processed by the chunker.
  - Chunker [[Chunker]]
    The chunker is responsible for breaking down the documents into smaller chunks, which are then processed by the embedder.
  - Enricher [[Enrichment]]
    The enricher is responsible for enriching the documents with additional information, such as entities, relationships, and concepts.
  - Embedder [[Embedder]]
    The embedder is responsible for generating text-embeddings and storing them in a vector database.
    **_ Here you can configure the embedding model, our default is snowflake-arctic model, but we can also generate custom embedding models for specific use cases._**
- as more files you add as longer the processing will take

  **_ Useful links _**

### Knowledge layer

**_ Useful links _**

- [Course for RAG and Finetuning](https://www.linkedin.com/learning/rag-fine-tuning-advanced-techniques-for-accuracy-and-model-performance/welcome-to-rag-and-finetuning?u=87878658)

### Model layer

### Agentic layer

## Flow Standalone X-Stream
