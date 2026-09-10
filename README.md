# Vision-Based Safety Lapse & Fraud Detection During Vehicle Refueling 🚗⛽

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Flask](https://img.shields.io/badge/Flask-Web_Framework-lightgrey)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Object_Detection-yellow)
![CNN](https://img.shields.io/badge/CNN-Deep_Learning-orange)

## 📌 Overview
An intelligent computer vision system engineered to detect safety lapses, monitor refueling compliance, and prevent fuel scams at petrol stations. Designed to utilize embedded vehicle sensors (such as the onboard cameras of a Renault vehicle), this project integrates advanced object detection and deep learning algorithms to ensure a safe, transparent, and compliant refueling experience.

> *Note: This project was created as part of ACE-Hacks 2025, conducted in collaboration with Renault's AI Lab.*

## 🚀 Key Features

*   **🔫 Nozzle Movement Detection (YOLOv8):** Real-time tracking of the fuel nozzle to ensure proper insertion into the fuel cap and to detect unsafe premature removals or unstable handling.
*   **⛽ Fuel Type Classification (CNN):** Accurately identifies the type of fuel being dispensed by classifying pump labels and nozzle colors to distinguish between **E5, E10, and E20 petrol**. Prevents engine damage by warning the driver of incorrect fuel types.
*   **🚗 Vehicle Movement Safety Checks:** Monitors the vehicle's stationary status during the fueling process. Triggers instant safety alerts if the car shifts, rolls, or attempts to move while the nozzle is engaged.
*   **💸 Anti-Scam Fuel Rate & Filling Check:** Uses computer vision and OCR to track the fuel pump meter, validating the dispensed volume against the displayed rate. This prevents common fuel scams, short-changing, or meter manipulation.
*   **🖥️ Real-time Web UI (Flask):** A responsive, live-feed dashboard built with Flask that displays the ongoing fueling status, live camera feeds, safety checkmarks, and instant anomaly alerts directly to the user.

## 🛠️ Technology Stack
*   **Core Vision:** YOLOv8 (Ultralytics), OpenCV
*   **Deep Learning:** Convolutional Neural Networks (CNNs), PyTorch
*   **Backend & Web UI:** Flask (Python), HTML, CSS, JavaScript
*   **Data Processing:** NumPy, Pandas

## 🏗️ System Architecture
1.  **Video Feed Ingestion:** Captures live feed from the car's side/rear-view camera array.
2.  **Object Detection Pipeline (YOLOv8):** Identifies the fuel nozzle, fuel pump meter, and their spatial relationship to the vehicle's fuel cap.
3.  **Classification Pipeline (CNN):** Crops the pump label region from the frame and passes it through a trained CNN to classify the ethanol blend (E5, E10, E20).
4.  **Meter Tracking:** Extracts fuel rate and quantity dispensed from the meter display to ensure mathematical consistency.
5.  **State Management & Alerting:** The Flask backend processes the vision pipeline's state in real-time and pushes updates (Safe / Warning / Scam Alert) to the frontend dashboard.

## 💻 Installation & Setup

```bash
# 1. Clone the repository
git clone [https://github.com/yourusername/Vision-Based-Safety-Lapse-Detection-During-Vehicle-Refueling.git](https://github.com/yourusername/Vision-Based-Safety-Lapse-Detection-During-Vehicle-Refueling.git)
cd Vision-Based-Safety-Lapse-Detection-During-Vehicle-Refueling

# 2. Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# 3. Install required dependencies
pip install -r requirements.txt

# 4. Download YOLOv8 & CNN weights
# Place your trained `best.pt` for YOLO and `cnn_model.pth` in the 'models/' directory.

# 5. Run the Flask application
python app.py
