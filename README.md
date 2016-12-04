# MySimpleRFMdongle
This is a 32bit ATSAM USB dongle with radio footprint for RFM69 or Lora Long range RFM95.

My main use is mini Serial Mysensors GW, and sniffer/debug tool with MYSController. etc.
Not a fancy thing, but I use it, and it didn't take lot of space on a panel when i ordered it so, why not :)

Tested with RFM69 and RFM95.
Just plug it, no usb cable!

Revision 1
<img src="https://raw.githubusercontent.com/scalz/MySimpleRFMdongle/development/img/MySimpleRFMdongle_rev1.jpg" alt="dongle rev1">

Revision 2
<img src="https://raw.githubusercontent.com/scalz/MySimpleRFMdongle/development/img/MySimpleRFMdongle_rev2.png" alt="dongle rev2">
Not assembled yet

		
###General 
------

|General spec.|  |
|---|---|---|
|Size |42.5*16.9 (mm) |
| MCU |ARM M0+ ATSAMD21E16/17/18 (same family as Arduino Zero but with 32pins) |
| Eeprom | EUI64 Eeprom |
| Authentication security | ATSHA204A chip footprint |
| Onboard led | WS2812B RGB |
| USB | USB A male connector. Sketch can be uploaded by native usb (like Arduino Zero) |
| Radio | RFM69HCW or RFM95W. SMA connector |
| Misc | Reset button |

####Onboard safety:
- Fuse + ESD protection for USB
- USB filtering

####Extension Connectors description
- Pogo pins for Cortex SWD programming
- USB for uploading sketch

####Arduino Pin description
| Arduino Pin | Description |
|---|---|---|
| 5 | Radio Interrupt Pin |
| 7 | ATSHA204A sot23 ic pin (for authentication) |
| 9 | Radio Reset Pin |
| 18 | Radio MOSI |
| 19 | Radio SCK |
| 22 | Radio MISO |
| 23 | Radio SS |
| 28 | WS2818B RGB led pin |
| 30 | SWCLK to Pogopins |
| 31 | SWDIO to Pogopins |

####Burning USB-CDC bootloader and Arduino 

I'm using Mattairtech variant board.
To find, bootloaders files and get all infos, please read : https://github.com/mattairtech/ArduinoCore-samd

Personally, I have no Atmel Ice. I use a Segger Jlink OB. It also exists cheap JTAG-SWD programmer which should work but I have not tried yet.

Simplified steps for burning bootloader with Segger Jlink OB (for more details, see links above):
1. Get a JTAG-SWD programmer. There are some cheap.
2. Download, install, and launch Atmel Studio
3. Connect your programmer to the JTAG port of the dongle
4. In Atmel Studio, go to Tools\Device Programming\ and Select your tools (the programmer), Device for MCU, Interface and apply. 
5. Try to read Id of MCU. It should be ok.
6. Then, still in the same dialog, click on Memories. Select the .hex of the bootloader you want to burn, and click Program. Then you can read, verify etc..

Then you have to install mattairtech usb driver, and boards in Arduino Ide through Boards Manager (Arduino ATSAM, and mattairtech ATSAM D21). For more details, see link above.

####Example sketch 

The example sketch is for Mysensors v2.x. This is simply the Serial GW sketch with the define for the pins. And you can add Neopixel lib.

###Overview
------

<img src="https://raw.githubusercontent.com/scalz/MySimpleRFMdongle/development/img/schematic.png.jpg" alt="schematic">

In Mysensors Serial GW mode, debugging another atsam Mysensors node. 
<img src="https://raw.githubusercontent.com/scalz/MySimpleRFMdongle/development/img/gw_with_node.jpg" alt="gateway mode">

###Known issues
------ 

###TODO
------
- upload STL

###Donations
------

I'm trying to make opensource projects. I do this for free and sharing spirit. I don't do ads etc..
But if you think information here is worth of some money, or want to reward me, feel free to send any amount through paypal.

[![](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=PWVDL2P64FDVU)  

Or you can also order pcb here :
I will earn a little percentage that will allow me to order proto pcb and share more fun design.

Or pay me a protein smoothie if you see me! oh well, a beer is ok too :)

### Contributors
------
Always special thanks to:
- Mysensors Team for its great work
- Mattairtech, Adafruit, Sparkfun, TI, Atmel etc.. for all educational infos they share

###Links, reference and license
------
- https://www.openhardware.io/view/82/My-simple-sniffer-dongle

Copyright Scalz (2016). released under the CERN Open Hardware Licence v1.2
