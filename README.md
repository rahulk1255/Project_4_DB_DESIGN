# 📌 Comic-Con Multi-Zone Parking System – ER Diagram

## 🧠 Overview
This project models a **scalable, multi-zone parking management system** designed for large-scale events like Comic-Con. It supports high traffic, multiple vehicle types, reserved parking, and dynamic spot allocation.

---

## 🎯 Objectives
- Track vehicle entry and exit  
- Support multiple visits per vehicle  
- Allocate parking dynamically  
- Handle reserved categories (VIP, staff, exhibitors, EV)  
- Maintain real-time availability  
- Record sessions and generate tickets  
- Manage payments and pricing  

---

## 🏗️ Core Entities

### 🚗 Vehicles & Categories
- **vehicles** → stores vehicle details  
- **vehicle_categories** → bike, car, SUV, EV  

---

### 🏢 Parking Infrastructure
- **parking_facilities** → venue abstraction  
- **parking_zones** → zone divisions  
- **parking_levels** → multi-level structure  
- **parking_spots** → individual parking slots  
- **parking_spot_categories** → defines spot types  

---

### 🔐 Access Control
- **access_categories**:
  - VIP  
  - Exhibitor  
  - Staff  
  - Cosplayer  

Used at both:
- Spot level (reserved infrastructure)  
- Session level (user privilege)  

---

### 🔄 Compatibility Mapping
- **vehicle_spot_compatibility**
  - Maps vehicle types to valid parking spot types  
  - Provides flexibility instead of hardcoding  

---

### 🅿️ Parking Operations
- **parking_sessions**
  - Tracks entry and exit  
  - One vehicle → multiple sessions  

- **spot_allocations**
  - Decouples spot assignment  
  - Supports reassignment and tracking  

- **parking_tickets**
  - Issued at entry  
  - Linked to session  

---

### 💳 Payments & Pricing
- **payments**
  - Stores payment details  
  - Supports multiple attempts  

- **pricing_rules**
  - Base price  
  - Hourly rate  
  - Surge multiplier  

---

## 🔗 Relationships
- One **vehicle** → many **sessions**  
- One **session** → many **spot allocations**  
- One **spot** → reused across sessions  
- **Zone → Level → Spot** hierarchy  
- One **session** → one **ticket**  
- One **session** → multiple **payments**  

---

## ⚙️ Key Design Decisions

### ✅ Decoupled Spot Allocation
Spot assignment is handled separately using `spot_allocations`.

### ✅ Derived Availability
Availability is calculated dynamically (no stored flag).

### ✅ Multiple Visits Support
Each visit is a separate parking session.

### ✅ Reserved Parking Support
Handles both reserved spots and privileged users.

### ✅ Scalable Architecture
Supports multi-zone, multi-level, and multi-facility setups.

### ✅ Flexible Pricing Model
Supports hourly and surge-based pricing.

---

## 📊 Example Queries
- Vehicles currently parked  
- Available parking spots  
- Revenue reports  
- Zone/level usage  
- Vehicle type analytics  

---

## 🚀 Conclusion
This ER design is **scalable, normalized, and production-ready**, capable of handling real-world event parking systems with dynamic allocation, access control, and payment tracking.
