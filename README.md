# HeartShield ❤️🛡️
### AI-Powered Cardiovascular Risk Assessment & Medical Report Analysis Platform

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0%2B-black.svg)](https://flask.palletsprojects.com/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-1.6%2B-orange.svg)](https://scikit-learn.org/)
[![Firebase](https://img.shields.io/badge/Firebase-Auth-yellow.svg)](https://firebase.google.com/)
[![EasyOCR](https://img.shields.io/badge/EasyOCR-Ready-green.svg)](https://github.com/JaidedAI/EasyOCR)
[![License](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)

**HeartShield** is an advanced, end-to-end intelligent cardiovascular healthcare platform designed to democratize early heart disease risk detection. By combining machine learning risk stratification, automated medical report parsing via OCR, secure Firebase authentication, and interactive health tracking, HeartShield empowers patients and clinicians with actionable cardiovascular insights.

---

## 🌟 Key Features

### 1. 🫀 Machine Learning Risk Stratification
- **10-Year Coronary Heart Disease Prediction**: Built on the clinically recognized Framingham Heart Study dataset.
- **Multi-Factor Risk Analysis**: Evaluates 15 critical demographic, lifestyle, and biochemical parameters.
- **Granular Classification**: Categorizes risk into 4 levels:
  - 🟢 **Low Risk** (< 25%)
  - 🟡 **Moderate Risk** (25% – 50%)
  - 🟠 **High Risk** (50% – 75%)
  - 🔴 **Very High Risk** (> 75%)
- **Actionable Health Insights**: Delivers tailored precautions and dietary/lifestyle guidance based on individual flags (e.g., elevated systolic BP, high cholesterol, diabetes).

### 2. 📄 Smart Medical Report OCR & Document Parsing
- **Automated Parameter Extraction**: Users can upload lab reports (Images: `.jpg`, `.png` or Word Documents: `.docx`).
- **EasyOCR & Regex Pipeline**: Automatically identifies and extracts clinical vitals (blood pressure, total cholesterol, glucose, heart rate, BMI, smoking status) and pre-fills the assessment form.
- **Privacy-First Processing**: Uploaded documents are parsed in a secure temporary buffer and instantly unlinked from storage once values are extracted.

### 3. 🔐 Dual-Layer Authentication & User Profiles
- **Client-Side Firebase Auth**: Modern authentication experience with email/password registration, login, and secure password reset.
- **Server-Side Token Verification**: Validates Firebase ID tokens via the Firebase Admin SDK and seamlessly establishes Flask-Login sessions.
- **Customizable Profiles**: Users can manage their account details and upload custom profile pictures.

### 4. 📊 Longitudinal Health Analytics Dashboard
- **Historical Tracking**: Stores past assessments and risk metrics chronologically in SQLite via SQLAlchemy.
- **Visual Risk Progression**: Interactive charts displaying trends across recent assessments.
- **Biometric History**: Review historical input records to track health improvements over time.

### 5. 💬 Interactive Health Assistant (Chatbot)
- Embedded instant assistant providing quick explanations on common cardiovascular symptoms, dietary precautions, and healthy lifestyle habits.

---

## 🛠️ Technology Stack

| Layer | Technologies |
| :--- | :--- |
| **Backend Web Framework** | [Flask](https://flask.palletsprojects.com/), [SQLAlchemy](https://www.sqlalchemy.org/), [Flask-Login](https://flask-login.readthedocs.io/), [Flask-Bcrypt](https://flask-bcrypt.readthedocs.io/) |
| **Machine Learning** | [Scikit-Learn](https://scikit-learn.org/), [NumPy](https://numpy.org/), [Joblib](https://joblib.readthedocs.io/) |
| **OCR & Document Processing** | [EasyOCR](https://github.com/JaidedAI/EasyOCR), [PyTorch](https://pytorch.org/), [python-docx](https://python-docx.readthedocs.io/) |
| **Authentication & Cloud** | [Firebase Authentication](https://firebase.google.com/products/auth), [Firebase Admin SDK](https://firebase.google.com/docs/admin/setup) |
| **Frontend** | HTML5, CSS3 (Modern Glassmorphism & Responsive Design), Vanilla JavaScript (ES6+), FontAwesome |
| **Database** | SQLite3 (`database.db`) |

---

## 🧬 Machine Learning Feature Architecture

The predictive engine processes 15 standardized clinical indicators normalized with `StandardScaler`:

| Parameter | Type | Clinical Description |
| :--- | :--- | :--- |
| `male` | Binary (0/1) | Biological sex (0 = Female, 1 = Male) |
| `age` | Integer | Patient age in years |
| `education` | Categorical (1-4)| Education level indicator |
| `currentSmoker` | Binary (0/1) | Current smoking status |
| `cigsPerDay` | Integer | Average cigarettes consumed per day |
| `BPMeds` | Binary (0/1) | Whether patient takes blood pressure medication |
| `prevalentStroke` | Binary (0/1) | History of stroke |
| `prevalentHyp` | Binary (0/1) | Prevalent hypertension diagnosis |
| `diabetes` | Binary (0/1) | Diabetic diagnosis |
| `totChol` | Float | Total serum cholesterol level (mg/dL) |
| `sysBP` | Float | Systolic blood pressure (mmHg) |
| `diaBP` | Float | Diastolic blood pressure (mmHg) |
| `BMI` | Float | Body Mass Index ($kg/m^2$) |
| `heartRate` | Float | Resting heart rate (beats per minute) |
| `glucose` | Float | Fasting blood glucose level (mg/dL) |

---

## 📂 Project Structure

```plaintext
heartshield_project/
├── app.py                            # Primary Flask application and routing logic
├── database.db                       # SQLite database storing users and assessments
├── heart_model.joblib                # Serialized Logistic Regression predictive model
├── scaler.joblib                     # Serialized StandardScaler for input features
├── firebase-service-account-key.json # Firebase Admin SDK service credentials (secret)
├── package.json                      # Frontend dependency configuration
├── package-lock.json                 # Lockfile for client assets
├── .gitignore                        # Git ignore specifications
├── uploads/                          # Temporary directory for uploaded lab reports
├── static/                           # Static assets
│   ├── heart.jpg                     # Branding & landing hero imagery
│   └── profile_pics/                 # User avatar uploads
└── templates/                        # Jinja2 HTML templates
    ├── home.html                     # Landing page with interactive hero & feature highlights
    ├── login.html                    # Firebase login with animated UI
    ├── signup.html                   # User registration page
    ├── dashboard.html                # User dashboard with trends & assessment history
    ├── assessment.html               # Assessment form with file upload / OCR integration
    ├── result.html                   # Detailed risk report, metrics & lifestyle guidance
    ├── profile.html                  # User profile and picture management
    └── layout.html                   # Base template layout
```

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10+** (Tested on Python 3.12)
- **Git**
- **pip** package manager

### 1. Clone the Repository

```bash
git clone https://github.com/samyuthavangari/heart-disease-predictor.git
cd heart-disease-predictor
```

### 2. Set Up a Virtual Environment

```bash
# Windows (PowerShell)
python -m venv venv
.\venv\Scripts\Activate.ps1

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install flask flask-sqlalchemy flask-login flask-bcrypt scikit-learn numpy joblib easyocr python-docx firebase-admin python-dotenv werkzeug
```

### 4. Environment & Firebase Configuration

1. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```
2. Populate your `.env` file with your secret key and Firebase credentials:
   ```env
   SECRET_KEY=your_secure_secret_key
   PORT=5001
   FIREBASE_SERVICE_ACCOUNT_KEY_PATH=firebase-service-account-key.json
   FIREBASE_API_KEY=your_firebase_api_key
   FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
   FIREBASE_PROJECT_ID=your_project_id
   FIREBASE_STORAGE_BUCKET=your_project.firebasestorage.app
   FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
   FIREBASE_APP_ID=your_firebase_app_id
   ```
3. Place your Firebase Admin service account key JSON file in the root directory (matching `FIREBASE_SERVICE_ACCOUNT_KEY_PATH`).

### 5. Run the Application

```bash
# Default (runs on port 5001 or configured PORT)
python app.py

# Custom port example:
$env:PORT = "5000"; python app.py
```

Open your browser and navigate to:
```
http://127.0.0.1:5001
```

---

## 📡 API & Key Routes Overview

| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | Landing page | Public |
| `GET` | `/login` | User login portal | Public |
| `GET` | `/signup` | User signup portal | Public |
| `POST` | `/firebase-auth` | Verifies Firebase ID token & sets session | Public (Token required) |
| `GET` | `/logout` | Clears active session | Authenticated |
| `GET` | `/dashboard` | User dashboard with metrics & chart trends | Authenticated |
| `GET`, `POST` | `/assessment` | Risk calculation form & model evaluation | Authenticated |
| `POST` | `/ocr-process` | Uploads and extracts metrics from lab files | Authenticated |
| `GET` | `/result/<id>` | Comprehensive risk evaluation results page | Authenticated |
| `GET` | `/profile` | Profile viewing & assessment history | Authenticated |
| `POST` | `/profile/update_pic`| Updates profile picture avatar | Authenticated |
| `POST` | `/chat` | Medical query chatbot endpoint | Public |

---

## 🔒 Security & Privacy Practices

- **Zero-Storage for OCR Documents**: Medical files submitted to `/ocr-process` are stored temporarily in `uploads/` only during processing and unlinked immediately in the `finally` block.
- **Firebase Token Verification**: Passwords are never sent or stored on the application server. Authentication is cryptographically verified through Firebase Admin SDK.
- **Session Protection**: Protected endpoints enforce `@login_required` decorators with CSRF and session validation.

---

## 👥 Contributors & Contact

- **Name**: samyuthavangari
- **Email**: [pranthi.vangari@gmail.com](mailto:pranthi.vangari@gmail.com)
- **Repository**: [https://github.com/samyuthavangari/heart-disease-predictor](https://github.com/samyuthavangari/heart-disease-predictor)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
