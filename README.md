# Security System README

This README provides an overview of the Security System, a project that employs multiple ultrasonic sensors and SONAR technology. The system includes two main components, each with its own functionality:

## Project Structure

### ESP32_Bluetooth_RFID_AccessPanel
- **bluetooth.h**: Header file for Bluetooth communication.
- **ESP32_Bluetooth_RFID_AccessPanel.ino**: Main Arduino sketch for the access panel.
- **lcd.h**: Header file for LCD interface.
- **rfid.h**: Header file for RFID sensor.
- **servo.h**: Header file for servo motor control.

### Multi_SONAR_Security_Sensor
- **Multi_SONAR_Security_Sensor.ino**: Main Arduino sketch for the multi-sonar security sensor.
- **sonar.h**: Header file for handling sonar sensors.

## ESP32_Bluetooth_RFID_AccessPanel

### Bluetooth Communication
- The `BluetoothSerial` library is used for Bluetooth communication.
- The device is named "ACCESS-PANEL-5".
- It listens for Bluetooth data and stores it in a global buffer.

### Wi-Fi Setup
- The system connects to a Wi-Fi network with the SSID "HotelSensorGrid" and the password "1234567890."

### Initialization
- The `setup` function initializes the LCD, RFID sensor, servo motor, and Bluetooth communication.
- A "LOADING" message is displayed on the LCD during the initialization process.

### Access Control Methods
- The system provides two access control methods:
  - RFID Access: It reads RFID card data and displays access information on the LCD.
  - Bluetooth Access: It reads data from the Bluetooth buffer and displays access information on the LCD.

### Data Retrieval
- The system retrieves sensor data from the server at "http://192.168.4.1/sensors."
- This data is displayed on the serial monitor.

### Commands
- The system can receive commands over the serial interface:
  - 0x58: Drives the servo to 0 degrees.
  - 0x55: Drives the servo to 0 degrees, delays 2 seconds, and then drives it to 90 degrees.
  - 0x4C: Drives the servo to 90 degrees.

### LCD Interface
- The system uses an I2C LCD (LiquidCrystal_I2C) for display.
- Various LCD functions are provided for printing and controlling the display.

## Multi_SONAR_Security_Sensor

### Wi-Fi Setup
- The system creates an access point with the SSID "HotelSensorGrid" and the password "1234567890."

### SONAR Sensors
- The system uses four SONAR sensors to measure proximity.
- Proximity values are acquired from the sensors and sent as a string.

### LED Indicator
- A digital pin (D4) is used as an LED indicator to blink at regular intervals.

### Web Server
- The system runs an ESP8266 web server on port 80.
- It responds to the "/sensors" endpoint by sending the proximity data.

## Setup and Usage

### ESP32_Bluetooth_RFID_AccessPanel
1. Load the `ESP32_Bluetooth_RFID_AccessPanel.ino` sketch onto your ESP32 microcontroller using the Arduino IDE or a compatible programming environment.
2. Configure the Wi-Fi settings in the code.
3. Install the required libraries for Bluetooth and LCD, if not already installed.
4. Flash the ESP32 with the sketch, and it will establish Wi-Fi and Bluetooth connections for access control.

### Multi_SONAR_Security_Sensor
1. Load the `Multi_SONAR_Security_Sensor.ino` sketch onto your ESP8266 microcontroller.
2. Configure the Wi-Fi settings in the code.
3. Install the required libraries for the SONAR sensor.
4. Flash the ESP8266 with the sketch, and it will create a Wi-Fi access point and serve proximity sensor data.

## Notes
- The ESP32 access panel provides access control through both RFID and Bluetooth communication, and it can display sensor data from the server.
- The multi-SONAR sensor provides proximity data through a web server, indicating the presence of objects or individuals in proximity to the sensors.

Please ensure that you have the required hardware and libraries to run these projects.
