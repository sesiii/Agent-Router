# 🌩️ Agent-Router: Cost-Optimized Dynamic LLM Router for the cloud

![License](https://img.shields.io/badge/License-MIT-blue.svg) [![Multi-Agent Systems](https://img.shields.io/badge/Field-Multi--Agent_Systems-green)](https://github.com/topics/multi-agent-systems) [![Cloud Computing](https://img.shields.io/badge/Domain-Cloud_Computing-purple)](https://github.com/topics/cloud-computing) [![LLM Routing](https://img.shields.io/badge/Technology-LLM_Routing-orange)](https://github.com/topics/llm)

**Agent-Router** is an intelligent, context-aware routing framework to select most optimal LLM deployed in the cloud. It dynamically evaluates user intent and system constraints to route queries to the most optimal Large Language Model (LLM) deployed across cloud infrastructure, **strictly optimizing for cost, latency, and required reasoning capability.**

Building upon foundational research in heterogeneous agent topologies, this project focuses on live, cloud-native cost management and dynamic selection, leveraging pre-existing benchmark data.

---

## 🧠 The Cloud AI Problem

As AI Systems scale in production, homogeneous architectures (using a single flagship LLM for every task) introduce severe inefficiencies:
* **Cost Bloat:** Using a frontier model (e.g., GPT-4 class) for simple data extraction tasks destroys profit margins.
* **Latency Bottlenecks:** Heavy reasoning models introduce unnecessary latency for tasks that require speed over deep logic.
* **Vendor Lock-in:** Relying on a single cloud provider limits access to specialized, open-source models deployed on alternative infrastructure.

## 💡 The Solution: Intelligent Cloud Routing

We introduce an **Agentic Router** that acts as the gateway to your cloud deployments. Instead of hardcoding LLM endpoints, the router uses the **Model Context Protocol (MCP)** to fetch metrics from a comprehensive benchmark database and dynamically selects the best tool for the job.

### Core Innovation: The Context-to-Cost Matrix
The orchestrator agent calculates a weighted score for every available cloud-deployed model based on:
1.  **User Intent & Domain:** (e.g., Is this a complex math problem or a simple text summarization?)
2.  **Live Cloud Economics:** (e.g., Cost per 1k tokens, provider rate limits).
3.  **Performance Constraints:** (e.g., Strict latency requirements vs. maximum accuracy).

---

## ⚙️ System Architecture

![System Architecture](https://github.com/sesiii/Agent-Router/blob/main/agent.png) 


### 1. LangGraph Orchestrator
The brain of the system. It intercepts the user query, classifies the intent, and determines the necessary threshold for accuracy vs. cost. 

### 2. The Knowledge Base: MCP-Powered Benchmark Database
Instead of running expensive evaluations at runtime, this framework relies on an **MCP Server** connected to a rich database of LLM benchmarks. 
* The database contains historical performance data (Accuracy, Peak Memory, Latency) for various models across highly specific domains (Medical, Finance, Mathematics, Coding, etc.).
* The MCP server exposes this data via secure tool calls, allowing the orchestrator to instantly pull the exact metrics needed to make an informed routing decision.

### 3. Dynamic Normalization Engine
A custom scoring algorithm that scales wildly different metrics (Cost in fractions of a cent, Latency in milliseconds, Accuracy as a percentage) into a normalized `[0, 1]` index to execute the mathematically optimal routing decision.

---

## 🚀 Workflow Execution

1.  **Ingestion:** Query hits the AI application in the cloud.
2.  **Intent Mapping:** The Agentic Router evaluates the prompt's complexity and maps it to a specific domain (e.g., `Domain: Medical`, `Subdomain: Diagnostics`).
3.  **MCP Metric Fetch:** The router queries the MCP server, which dips into the benchmark database to return the historical accuracy and latency for all candidate models in that specific domain.
4.  **Cost-Benefit Calculation:** Models are scored. If the task is simple, high-cost frontier models are heavily penalized in favor of faster, cheaper alternatives.
5.  **Execution:** The payload is routed to the winning cloud endpoint.
6.  **Aggregation:** Results are seamlessly returned to the pipeline.

---

## 🚧 Roadmap & Future Extensions

- [x] Integrate LangGraph orchestrator with MCP tools.
- [x] Establish the MCP server as the bridge to the benchmark database.
- [x] Implement dynamic weighting for Cost vs. Accuracy.
- [ ] **Live API Pricing Hooks:** Connect the MCP server to live cloud pricing APIs for real-time cost fluctuations.
- [ ] **Cold-Start Mitigation:** Factor model loading times into the latency score for serverless deployments.

---

**Disclaimer:** This is an active research prototype. Cloud routing configurations should be thoroughly tested before deployment in strict production environments.