# Crashfree India Dashcam Traffic Intelligence System
## AI-Based Traffic Violation Detection, Vehicle Analytics, and Road Event Dashboard

## Overview

This project is an end-to-end computer vision pipeline developed for the Crashfree India Founder’s Office assignment. The system analyzes dashcam footage from Indian roads and automatically detects traffic violations, tracks vehicles, generates analytics, and produces an interactive dashboard.

The pipeline is optimized for practical deployment using pretrained deep learning models, GPU inference, lightweight post-processing heuristics, and dashboard visualization.

The system processes a raw dashcam video and produces:

- Structured JSON analytics output
- Traffic violation detections
- Vehicle classification and de-duplication
- Traffic density trends
- Junction analysis support
- Top annotated evidence frames
- Interactive HTML dashboard
- Downloadable packaged deliverables

---

# Core Features

## 1. Traffic Violation Detection

The system detects the following violations:

### Helmet-less Riding
Detects riders or pillion passengers on two-wheelers without helmets.

Output:
- Total count
- Timestamp of each occurrence
- Confidence score
- Bounding box
- Top 3 evidence frames

Detection logic:
- Motorcycle detected
- Person detected overlapping motorcycle
- Heuristic helmet absence inferred

---

### Triple Riding
Detects three or more riders on a two-wheeler.

Output:
- Count
- Timestamp
- Confidence
- Bounding boxes
- Top evidence frames

Detection logic:
- Motorcycle detection
- Person overlap clustering
- Rider count threshold

---

### Wrong-Side Driving
Detects vehicles moving against inferred traffic flow.

Output:
- Count
- Timestamp
- Vehicle bounding box
- Evidence frames

Detection logic:
- Object tracking
- Direction vector estimation
- Flow mismatch detection

---

### Signal Jumping
Detects vehicles crossing under red-light conditions.

Output:
- Count
- Timestamps
- Bounding boxes
- Event logs

Detection logic:
- Traffic light detection
- Vehicle position tracking
- Stop-region crossing inference

---

### Mobile Phone Use While Driving
Attempts to detect visible mobile usage by drivers.

Output:
- Count
- Timestamp
- Confidence
- Bounding box

Detection logic:
- Driver/person detection
- Hand-object proximity heuristics

---

# 2. Vehicle Detection & Classification

Vehicles are detected, classified, and tracked across frames.

Supported categories:

### Two Wheeler
Includes:
- Motorcycles
- Scooters
- Mopeds

---

### Light Motor Vehicle (LMV)
Includes:
- Cars
- Jeeps
- Taxis
- Vans
- Auto-rickshaws

---

### Heavy Motor Vehicle (HMV)
Includes:
- Trucks
- Buses
- Tankers
- Large transport vehicles

---

### Others
Includes:
- Bicycles
- E-rickshaws
- Construction vehicles
- Unknown moving objects

---

Generated metrics:
- Unique vehicle count
- Category-wise distribution
- Percentage share
- Density over time

---

# 3. Junction Detection Support

The current implementation provides a semi-automated junction review pipeline.

Supported junction classes:

- T-junction
- 4-way intersection
- X-junction
- Y-junction
- Roundabout
- Flyover entry
- Underpass entry

Workflow:
- Periodic frame extraction
- CSV review template generation
- Manual classification support
- Integration into final dashboard

This hybrid design reduces implementation complexity while preserving deliverable completeness.

---

# 4. Interactive Dashboard

Generated HTML dashboard includes:

- Summary metric cards
- Violation distribution chart
- Vehicle category breakdown
- Density timeline
- Event log
- Junction log
- Clickable timestamp event explorer

Export:
```bash
dashboard.html
