# Azure AI Search Automation Workflow

## Architecture diagram
![AI Link Fixer Architecture](docs/architecture/ai-link-fixer-architecture.png)

## Overview
This workflow automates the creation of Azure AI Search resources including:
- Data Source
- Skillset (Azure OpenAI Embedding)
- Index
- Indexer
- Vector Search configuration (HNSW + Azure OpenAI Vectorizer)
- Environment-specific deployments (Dev, PerfTesting, UAT, Staging, Prod)

The workflow is triggered manually using *workflow_dispatch*.

## Features
- Multi-environment deployment using GitHub Action inputs
- OIDC-based Azure Authentication (no secrets needed)
- Azure OpenAI embedding skill for vector generation
- Semantic ranking + vector search support
- Integration with SQL Database as the search source
- Fully automated repeatable provisioning

## Required GitHub Secrets
- AZURE_CLIENT_ID
- AZURE_TENANT_ID
- AZURE_SUBSCRIPTION_ID
- AZURE_SEARCH_API_KEY
- RG_NAME

## Required GitHub Variables
- SQL_SERVER_NAME
- SQL_DB_NAME
- SEARCHSERVICE_NAME
- OPENAI_URI
- SKILLSET
- INDEX
- INDEXER
- DATASOURCE
- VECTORCONFIG
- VECTORPROFILE
- VECTORIZER

## Triggering Deployment
Go to:

**GitHub → Actions → Create Azure AI Search Resources → Run Workflow**

Select your environment:
- Dev
- PerfTesting
- Uat
- Staging
- Prod

## Output
Once executed, the workflow will:
1. Create or update the DataSource  
2. Create the Skillset with Azure OpenAI embedding  
3. Create the Index with semantic + vector search  
4. Configure vector search algorithms & profiles  
5. Create and attach the Indexer  

This ensures a consistent search experience across all environments.