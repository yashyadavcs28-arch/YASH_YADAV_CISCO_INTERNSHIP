# 🌐 NetSage AI

## AI-Assisted Network Troubleshooting System with Human Review

NetSage AI is a Python-based network troubleshooting prototype designed to assist users in identifying common Cisco-style networking problems.

The system combines **deterministic Python rule checking**, an **AI-oriented diagnosis architecture**, and a **mandatory human review workflow**.

Instead of automatically applying network fixes, NetSage AI provides evidence-backed troubleshooting recommendations that are reviewed by a human before being considered final.

---

## 📌 Project Overview

Network troubleshooting can be challenging for junior network engineers because a single symptom may have multiple possible causes.

For example:

> A PC receives an IP address but cannot communicate with a server.

Possible causes include:

- VLAN configuration problems
- Incorrect default gateway
- DHCP problems
- DNS problems
- Routing issues
- Access Control Lists (ACLs)
- NAT configuration
- Wireless configuration

NetSage AI provides a structured approach to troubleshooting these scenarios.

The system analyzes:

1. Network symptoms
2. Topology information
3. Cisco-style `show` command output
4. Deterministic rule-checking results

It then produces a structured diagnosis containing:

- Likely root cause
- OSI layer
- Confidence score
- Supporting evidence
- Recommended next command
- Recommended fix steps

Every diagnosis requires **human review**.

---

# 🎯 Objectives

The main objectives of NetSage AI are:

- Analyze Cisco-style network troubleshooting scenarios.
- Identify common network configuration problems.
- Implement deterministic troubleshooting rules using Python.
- Provide structured diagnosis results.
- Identify the relevant OSI layer.
- Provide evidence supporting the diagnosis.
- Recommend the next troubleshooting command.
- Suggest appropriate remediation steps.
- Implement human-in-the-loop validation.
- Record human review decisions.
- Provide a web-based Streamlit interface.
- Provide basic dashboard analytics.
- Establish an architecture suitable for future real LLM integration.

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │    Network Case      │
                    │ Symptom + Topology   │
                    │   + Show Output      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Python Rule Checker │
                    │  Deterministic Rules │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Rule-Based Findings │
                    │ Issue / Evidence /   │
                    │ Recommendation       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Diagnosis Engine     │
                    │ AI / Mock AI Mode    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Structured Diagnosis │
                    │ Root Cause           │
                    │ OSI Layer            │
                    │ Confidence           │
                    │ Evidence             │
                    │ Next Command         │
                    │ Fix Steps            │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Human Reviewer     │
                    └──────────┬───────────┘
                               │
                  ┌────────────┼────────────┐
                  ▼            ▼            ▼
              Accepted       Edited      Rejected
                  │            │            │
                  └────────────┼────────────┘
                               ▼
                    ┌──────────────────────┐
                    │ Human Review Log     │
                    │ CSV Storage          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Dashboard / Analytics│
                    └──────────────────────┘
