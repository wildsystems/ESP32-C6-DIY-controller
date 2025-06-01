# ESP32-C6 Sensor Controller

## 📊 Description
This project is a basic controller built around the ESP32-C6-MINI-1, designed for monitoring and managing temperature, humidity, flow, and PWM-based sensors/actuators. It supports direct connection for four NTC thermistors, one DHT21 sensor, a 1-Wire bus with DS18B20, one pulse input for a Hall effect flow sensor, one PWM input, one PWM output, and two relay outputs. Additionally, it includes a USB-C connector for power and communication, supporting USB-CDC (virtual serial) and JTAG debugging.

---

## 🔧 Key Features

| Component               | Description                                            |
|------------------------|--------------------------------------------------------|
| 🌡️ 4x NTC Inputs         | Analog reading via voltage divider with fixed resistor |
| 🔋 1x DHT21 (AM2301)     | Temperature and humidity sensor                        |
| ❄️ 1x DS18B20 (1-Wire)   | Bus for Dallas 1-Wire temperature sensors              |
| 🚿 1x Flow Sensor (HALL) | Pulse-based flow measurement                           |
| 🎛️ 1x PWM Input           | Frequency or duty-cycle based input                   |
| 🔉 1x PWM Output          | PWM signal output for motor/valve control             |
| ⚙️ 2x Relay Outputs       | Load control (e.g. pump, valve)                        |
| 🔌 1x USB-C Connector     | Power input, USB-CDC serial, and JTAG debug support   |

---

## ⚙️ Example Pin Assignment (ESP32-C6-MINI-1 Safe GPIOs)

| Function                | GPIO Pin | Notes                                      |
|------------------------|----------|---------------------------------------------|
| NTC1 (analog in)       | GPIO1    | ADC1 channel                                |
| NTC2                   | GPIO3    | ADC1 channel                                |
| NTC3                   | GPIO4    | ADC1 channel                                |
| NTC4                   | GPIO5    | ADC1 channel                                |
| DHT21 / DS18B20        | GPIO6    | 4.7k pull-up to 3.3V                        |
| Flow Sensor (input)    | GPIO7    | Interrupt on rising edge                    |
| PWM Input              | GPIO14   | Timer capture capable                       |
| PWM Output             | GPIO15   | LEDC or MCPWM output                        |
| Relay 1 (output)       | GPIO18   | Load control                                |
| Relay 2                | GPIO19   | Load control                                |
| USB D+                 | GPIO13   | Native USB data+ (shared with UART RX)      |
| USB D−                 | GPIO12   | Native USB data−                            |

---

## 📝 Notes

- All GPIOs used are considered safe for ESP32-C6-MINI-1 boot operation.
- NTC sensors are read via the internal ADC1.
- DHT21 requires at least a 2-second interval between readings.
- DS18B20 supports multiple sensors on a single 1-Wire bus.
- Flow sensor input should have a pull-up if not already onboard.
- PWM input can be measured using capture/timer functionality.
- PWM output can be generated via LEDC or MCPWM peripheral.
- Relay outputs can be connected to opto-isolated relay modules.
- USB-C port supports 5V input and USB communication (CDC, JTAG).

---

## 🚀 Applications

- Fermentation controller
- Room temperature and humidity monitoring
- Smart irrigation systems
- General home automation
- Fan or valve modulation via PWM
- USB-connected data acquisition

---

## ⚠️ Future Improvements

- Wi-Fi and MQTT communication
- OTA updates
- Web interface for configuration and monitoring
- EEPROM or NVS-based configuration storage
