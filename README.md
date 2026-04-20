# AgriBench LLM Evaluation

This project evaluates two LLMs (LLaMA-3.3-70b and GPT-4o-mini) on 20 
agricultural Q&A questions from the AgriBench dataset. Each answer is 
scored by an LLM judge on 5 metrics: accuracy, relevance, completeness, 
conciseness, and interpretability.

## Setup
1. Add your API keys in the notebook:
   - OpenAI: https://platform.openai.com
   - Groq: https://console.groq.com

2. Place `Agribench Task.json` in your working directory.

## Design Decisions
Why these two models?
LLaMA (open-source, free) vs GPT-4o-mini (commercial) gives meaningfully 
different results due to different training data and RLHF approaches.

Why LLM-as-a-Judge?
Agricultural answers are open-ended. Rule-based metrics like BLEU only 
measure word overlap, not whether the answer is actually correct or useful.

Why GPT-4o-mini as judge?
Strong instruction-following for JSON output, cost-effective (~$0.03 total),
and different from one of the subject models (LLaMA) to reduce bias.

Why interpretability as 5th metric?
The other 4 metrics measure correctness and style, but not whether a 
non-expert farmer can actually understand the answer. Agricultural advice 
is only useful if the end user can follow it.
