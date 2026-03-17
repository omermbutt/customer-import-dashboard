# Customer Import Dashboard 📊

A FastAPI-powered web application for managing high-volume customer data imports into [Blueshift](https://getblueshift.com). Features real-time WebSocket progress tracking, bulk CSV validation, per-record API validation, and an Account Audit Dashboard tab.

## Features

### Import Dashboard
- **Bulk CSV Import** — upload and process large customer data files with field mapping and validation
- **Real-Time Progress Tracking** — WebSocket-based live updates showing import status row by row
- **Per-Record API Validation** — validate each record against the Blueshift GET API before committing
- **Error Reporting** — detailed per-row error logs with reason codes and failed field highlighting
- **Retry Logic** — selectively re-import failed records without re-processing successful ones

### Account Audit Dashboard
- **Account Health Overview** — snapshot of customer record completeness and data quality
- **Field Coverage Analysis** — identify missing or malformed fields across your customer base
- **Segment Readiness** — check whether records meet criteria for key audience segments

## Tech Stack

```
Backend:    Python · FastAPI · WebSocket
Validation: Blueshift REST API (GET /customers)
Data:       CSV processing · JSON parsing
Frontend:   HTML · CSS · JavaScript (Vanilla)
Transport:  WebSocket (real-time progress)
```

## Architecture

```
CSV Upload → Field Validation → API Validation (per record) → Import
                                      ↓
                              WebSocket → Live UI Progress
```

## Getting Started

```bash
git clone https://github.com/omermbutt/customer-import-dashboard.git
cd customer-import-dashboard
pip install -r requirements.txt
uvicorn main:app --reload
```

Then open `http://localhost:8000` in your browser.

## Configuration

Set your Blueshift API credentials in `.env`:

```
BLUESHIFT_API_KEY=your_api_key_here
BLUESHIFT_BASE_URL=https://api.getblueshift.com
```

## Background

Built to streamline enterprise client onboarding at [Blueshift](https://getblueshift.com) — replacing manual CSV uploads and one-off validation scripts with a reliable, auditable import pipeline. Iterated through multiple production use cases across media, finance, and e-commerce clients.

---

*Part of a broader internal tooling suite for enterprise data operations.*
