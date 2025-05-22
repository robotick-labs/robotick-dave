# 🧰 Dave – Device Abstraction and Validation Engine

*The gruff but dependable core of bare-metal robotics control.*

---

## What is Dave?

**Dave** is a lightweight, testable C++ abstraction layer for bare-metal microcontrollers.

Designed as part of the [Robotick Engine](https://github.com/robotick-labs/robotick), Dave provides clean, minimal APIs to access and validate low-level hardware peripherals such as:
- GPIO
- ADC
- PWM / Timers
- UART
- SPI / I2C
- and more...

Dave enables hardware logic to be:
- **Portable** across STM32 boards (and beyond)
- **Simulatable** for off-device testing
- **Validatable** via CI on real hardware grids
- **Composable** into Robotick workloads, or standalone

## Why "Dave"?

Because **Dave** is:

> 🧔 "That one engineer you trust to wire it right the first time."

The name stands for **Device Abstraction and Validation Engine**, but more importantly — *Dave is dependable*. Dave doesn’t need an RTOS. Dave doesn’t break abstraction layers. Dave just quietly gets the job done.

## Key Goals

- **💡 Minimal Overhead** – works on resource-constrained MCUs (e.g., STM32G4) without an RTOS
- **🧪 Unit-Test Friendly** – supports dependency injection and simulation of hardware interactions
- **🛠️ Pluggable HAL Backends** – use STM32 HAL today, custom MMIO tomorrow
- **🧱 Composable APIs** – integrates with Robotick's workload model or your own

## Current Status

| Feature        | Status     |
|----------------|------------|
| GPIO           | ✅ Working |
| PWM            | 🛠️ In progress |
| ADC            | 🛠️ In progress |
| UART           | 🔜 Planned |
| CI Integration | 🔜 Planned |
| DevGrid Support | 🔜 Planned |

---

## Example

```cpp
DaveGPIO led(GPIOB, GPIO_PIN_4);
led.setOutputMode();
led.write(true);
```

Or in test code:

```cpp
DaveMockGPIO led;
led.expectSetOutput().returns(true);
led.expectWrite(true);
```

---

## How It Fits

Dave is part of the **Robotick hardware stack**:

```
[ Robotick Workloads (C++) ]
         ↓
[ Dave Hardware Abstractions ]
         ↓
[ STM32 HAL or Custom Drivers ]
         ↓
[ Real Hardware (MCU) ]
```

---

## Roadmap

- [ ] Initial GPIO / ADC / PWM modules (STM32G4 target)
- [ ] Pure-mock test backends
- [ ] SimHost integration for CI/CD
- [ ] CLI utilities for flashing, probing, and logging
- [ ] Rust bindings?

---

## Contributions Welcome!

Want to add a backend? Test on new silicon? Improve the validation layer? [Join the devs](https://github.com/robotick-labs/robotick) and help make embedded robotics testable, composable, and fun.

---

## License

Apache License 2.0 (same as Robotick)

---

## Author

Built with ❤️ (and a soldering iron) by [Paul Connor](https://github.com/paulwconnor-ai) and the Robotick Labs community.
