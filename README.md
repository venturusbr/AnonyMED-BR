# AnonyMED-BR

# Guardians of the Data: Medical Record Anonymization in Brazilian Portuguese

This repository contains the resources, dataset, and code for the paper:  
**"Guardians of the Data: NER and LLMs for Effective Medical Record Anonymization in Brazilian Portuguese"**  
by Mauricio Schiezzaro, Guilherme Rosa, Helio Pedrini, and Bruno Augusto Goulart Campos.

📄 Published in *Frontiers in Public Health* (2025).  

---

## 🚀 Overview

Medical record anonymization is essential to protect patient privacy while enabling research and the development of AI solutions in healthcare.  
This project introduces **AnonyMED-BR**, a dataset for anonymization of medical records in **Brazilian Portuguese**, and evaluates different anonymization strategies based on **transformer models**.

We compare two complementary approaches:
- **Extractive anonymization**: identifying sensitive entities using NER-based models.  
- **Generative anonymization**: rewriting medical records with sensitive information replaced by tags.  

We also propose a novel **LLM-as-a-Judge evaluation framework**, using a reasoning LLM to assess anonymization quality, information loss, and re-identification risk.

---

## 📊 Dataset: AnonyMED-BR

- **2,962 medical records**:  
  - 1,075 real (from a Brazilian tertiary hospital)  
  - 1,887 synthetic (generated and validated using GPT-4o)  

- **Entities covered**: patient names, doctors, IDs, dates, hospitals, addresses, contact information, and other identifiers.  
- Annotation reached **95% inter-annotator agreement**.  
- The data complies with **LGPD (Brazil)** and **GDPR (EU)**.  

---

## 🧠 Models Evaluated

We benchmarked **extractive** and **generative** strategies across several models:

- **BERT-based**:  
  - BERTimbau-leNER 
  - mBERT  
  - BioBERTpt  

- **T5-based**:  
  - ptt5-v2   

- **GPT-based**:  
  - GPT-4o 
  - GPT-4o mini 

---

## 🔑 Key Findings

- **BERTimbau-leNER** achieved the best **overall performance** (F1 = 0.9270), particularly strong on synthetic data.  
- **GPT-4o** was the **best on real data** (F1 = 0.9356), highlighting its robustness to noisy and complex records.  
- **Synthetic data works**:  
  - mBERT trained only on synthetic records (**mBERT-syn**) outperformed mBERT trained only on real data.  
  - mBERT-syn (F1 = 0.9257 overall) nearly matched the top-performing models, showing synthetic data as a **viable alternative** when real data is scarce.  
- **Task-specific fine-tuning > domain pretraining**:  
  - NER fine-tuning (BERTimbau-leNER) gave better results than domain pretraining (BioBERTpt).  
- **LLM-as-a-Judge evaluation** using Gemini 2.5 Pro provided deeper insights into anonymization quality:  
  - GPT-4o scored highest in **information preservation** and **low re-identification risk**.  
  - Extractive models like BERTimbau-leNER offered strong local deployment options with good privacy guarantees.  

---

## 📈 Results Summary

| Model            | F1 (Overall) | F1 (Real) | F1 (Synthetic) |
|------------------|--------------|-----------|----------------|
| **BERTimbau-leNER** | **0.9270**   | 0.9007    | **0.9447**         |
| **GPT-4o**         | 0.9195       | **0.9356**| 0.9089         |
| ptt5-v2           | 0.8748       | 0.8794    | 0.8718         |
| GPT-4o mini       | 0.8595       | 0.8264    | 0.8759         |
| BioBERTpt         | 0.8523       | 0.8505    | 0.8535         |
| mBERT-syn         | 0.9257       | 0.8919    | -              |
| mBERT-real        | 0.8367       | 0.8804    | -              |

---

## 📦 Repository Contents

- **Dataset**: [AnonyMED-BR](https://github.com/venturusbr/AnonyMED-BR) (real + synthetic annotated records).  
- **Model configs**: Fine-tuning scripts for BERT, T5, and GPT evaluation.  
- **Evaluation framework**: Metrics (precision, recall, F1) + LLM-as-a-Judge.  
- **Results**: Entity-level and model-level comparisons.  

---

## 📌 Citation

If you use this dataset or models, please cite:  

```bibtex
@article{schiezzaro2025guardians,
  title={Guardians of the Data: NER and LLMs for Effective Medical Record Anonymization in Brazilian Portuguese},
  author={Schiezzaro, Mauricio and Rosa, Guilherme and Pedrini, Helio and Campos, Bruno Augusto Goulart},
  journal={Frontiers in Public Health},
  year={2025},
  publisher={Frontiers},
  url={https://github.com/venturusbr/AnonyMED-BR}
}
