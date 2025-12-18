# Battery Power Board

**Project:** Battery Power Board — power distribution, monitoring, and telemetry board for the University of Alberta EcoCar Prototype Vehicle.

**Vehicle:** Sally — 1st Place, Shell Eco-Marathon Hydrogen Prototype Category  
**Competition Year:** 2025

<p align="center">
  <img src="https://github.com/user-attachments/assets/3f554231-5f74-4615-ad5c-d05537680ecd" width="500">
</p>

---

## Overview

The Battery Power Board serves as the central power monitoring and distribution interface between the vehicle’s energy sources and downstream subsystems.  
It measures battery and regulated rail voltages and currents, monitors thermal conditions, computes energy usage, and communicates system status over the vehicle CAN bus.

---

## Key Functions

- Monitor battery input voltage and current
- Measure regulated output rails (12 V and 7 V)
- Monitor thermal conditions of critical power components
- Track energy consumption over time
- Display live system data on a local OLED
- Communicate telemetry and fault states over CAN bus
- Respond to vehicle safety events (e.g. hydrogen alarm)

---

## Power Architecture

### Input

- Battery input monitored via precision voltage divider
- Hall-effect current sensing for non-intrusive measurement
- Designed for continuous monitoring under dynamic load conditions

### Output Rails

- **12 V Rail**
  - Voltage and current monitored
  - Supplies downstream electronics and subsystems
- **7 V Rail**
  - Voltage and current monitored
  - Intended for low-power or auxiliary loads

Each rail is independently sensed to allow detailed power budgeting and diagnostics.

---

## Sensing & Measurement

### Electrical Measurements

The board continuously measures:

- Battery input voltage
- Battery input current
- 12 V output voltage
- 12 V output current
- 7 V output voltage
- 7 V output current

These measurements allow real-time estimation of power flow and system loading.

### Thermal Monitoring

- Multiple analog temperature sensors placed near:
  - Buck regulator
  - Output power stage
  - Control electronics
- Enables detection of abnormal thermal conditions during operation

---

## Energy Tracking

The board integrates measured voltage and current over time to estimate **energy usage (joules)**.  
This data is used for:

- Efficiency analysis
- Post-run performance evaluation
- Competition strategy optimization

---

## Local User Interface

- **SSD1306 OLED display**
- Displays:
  - Battery voltage and current
  - Output rail voltages and currents
  - Temperatures of key components
- Automatically switches to an alarm display when a fault condition is received

This allows quick diagnostics during testing without external tools.

---

## CAN Bus Integration

- Fully integrated into the vehicle **CAN network**
- Transmits:
  - Electrical measurements
  - Thermal data
  - System status flags
- Receives:
  - Safety and fault signals (e.g., hydrogen alarm)
  - Synchronization or status commands from other vehicle modules

The board reacts immediately to safety-critical CAN messages by updating system state and user display.

---
