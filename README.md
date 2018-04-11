# lora-feather-m0

## Example "lora-feather-m0-simple"

This example was tested on the Swisscom Low Power Network.

### Requirements
- Adafruit Feather M0 Adalogger (ada-2796)
- Adafruit FeatherWing LoRa Radio (ada-3231)
- [Arduino-LMIC library](https://github.com/matthijskooijman/arduino-lmic)

Some changes need to be done on the LMIC library:
- Setting the SPI clock speed in the HAL.cpp to 8MHZ
- Check the config.h settings (868MHz frequency and SX127x LoRa module)

### Wiring
![featherwing-lora-radio](https://github.com/trohrer/lora-feather-m0/blob/master/img/featherwing-lora-radio.png)

### Used Pins
```C
#define RFM95_CS  10  // "B"
#define RFM95_RST 11  // "A"
#define RFM95_INT 6 // "D"
#define RXTIMEOUT 9 // "C"

// LMIC Pin mapping  
const lmic_pinmap lmic_pins = {  
	.nss = RFM95_CS ,  
	.rxtx = LMIC_UNUSED_PIN,  
	.rst = RFM95_RST,  
	.dio = {RFM95_INT, RXTIMEOUT, LMIC_UNUSED_PIN}, // DIO0, DIO1, DIO2  
};
```
In LoRa mode the DIO pins are used as follows:  
DIO0: TxDone and RxDone  
DIO1: RxTimeout  
DIO2: not used


