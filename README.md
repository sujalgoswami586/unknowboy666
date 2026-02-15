# 🚗 Arduino Based Accident Alert System

## 📌 Project Description

This project is a vehicle Accident Detection and Emergency Alert System built using Arduino Nano.  
The system detects sudden impact using a 3-axis accelerometer and automatically sends the GPS location via GSM module (SIM800L) to a predefined emergency contact.

In case of crash detection:
- 🚨 Buzzer activates
- 📟 LCD displays crash status
- 📍 GPS location is fetched
- 📞 Emergency call is placed
- 📩 SMS with Google Maps link is sent

---

# 🧩 Hardware Components Used

- Arduino Nano (ATmega328P)
- SIM800L GSM Module
- NEO-6M GPS Module
- ADXL335 / GY-61 Accelerometer
- 16x2 I2C LCD Display
- Buzzer
- Push Button
- 18650 Li-ion Battery (for GSM)
- Connecting wires

---

# 🔌 Complete Pin Connections

## 🔹 1️⃣ Accelerometer (GY-61 / ADXL335)

| Accelerometer Pin | Arduino Nano Pin |
|-------------------|------------------|
| VCC               | 3.3V             |
| GND               | GND              |
| X_OUT             | A1               |
| Y_OUT             | A2               |
| Z_OUT             | A3               |

---

## 🔹 2️⃣ GPS Module (NEO-6M)

| GPS Pin | Arduino Nano Pin |
|----------|------------------|
| VCC      | 5V               |
| GND      | GND              |
| TX       | D8               |
| RX       | D9               |

(Using AltSoftSerial)

---

## 🔹 3️⃣ GSM Module (SIM800L)

| SIM800L Pin | Arduino Nano Pin |
|--------------|------------------|
| VCC          | External 4V Supply (18650 Battery) |
| GND          | GND              |
| TX           | D2               |
| RX           | D3               |

⚠ IMPORTANT:
- Do NOT power SIM800L directly from Arduino 5V.
- Use stable 3.8V–4.2V supply (Li-ion battery recommended).

---

## 🔹 4️⃣ I2C LCD (16x2)

| LCD Pin | Arduino Nano Pin |
|----------|------------------|
| VCC      | 5V               |
| GND      | GND              |
| SDA      | A4               |
| SCL      | A5               |

Common I2C addresses:
- 0x27
- 0x3F

---

## 🔹 5️⃣ Buzzer

| Buzzer Pin | Arduino Nano |
|------------|--------------|
| Positive   | D12          |
| Negative   | GND          |

---

## 🔹 6️⃣ Emergency Cancel Button

| Button Pin | Arduino Nano |
|------------|--------------|
| One Side   | D11          |
| Other Side | GND          |

(Using INPUT_PULLUP)

---

# ⚙️ Required Libraries

Before uploading the code, download required libraries from:

https://github.com/ahmadlogs/accident-alert-system/tree/main/libraries

## 📥 Installation Steps

1. Download library ZIP files.
2. Open Arduino IDE.
3. Go to:
   Sketch → Include Library → Add .ZIP Library
4. Install all libraries.
5. Restart Arduino IDE.

---

# 📚 Libraries Used

- TinyGPS++
- SoftwareSerial
- AltSoftSerial
- LiquidCrystal_I2C
- Wire (built-in)

---

# 🧠 Working Principle

1. Accelerometer continuously monitors X, Y, Z axis values.
2. Change in acceleration is calculated:
   Magnitude = √(dx² + dy² + dz²)
3. If magnitude exceeds defined threshold → crash detected.
4. Buzzer activates for 30 seconds.
5. GPS coordinates are fetched.
6. GSM module:
   - Makes emergency call
   - Sends SMS with Google Maps location link

Example SMS:

Accident Alert!!
http://maps.google.com/maps?q=loc:LATITUDE,LONGITUDE

---

# 🔧 Code Configuration

Update emergency number before uploading:
