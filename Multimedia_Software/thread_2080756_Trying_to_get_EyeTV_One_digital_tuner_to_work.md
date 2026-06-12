---
title: "Trying to get EyeTV One digital tuner to work"
date: 2012-11-04
forum: Multimedia Software
---

### Post by evil-boweevil on 2012-11-04
I've been trying to get ubuntu to recognize my eyetv one tuner.
I'm running on an older mac mini.  I can't get anything to show up under /dev/dvb

It looks like it's the same tuner as this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick#Firmware](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick#Firmware)

Here is the dmesg after I plug it in:

[ 2561.713138] usb 1-3: >Product: EyeTV One
[ 2561.713143] usb 1-3: >Manufacturer: Elgato
[ 2561.713148] usb 1-3: >SerialNumber: 000000be

and after lsusb:

eolson@PowderServer:/dev$ lsusb
Bus 001 Device 011: ID 0fd9:002b Elgato Systems GmbH
Bus 001 Device 009: ID 1058:0748 Western Digital Technologies, Inc.
Bus 001 Device 005: ID 1058:1010 Western Digital Technologies, Inc. Elements External HDD
Bus 002 Device 003: ID 17ef:6014 Lenovo Mini Wireless Keyboard N5901
Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks for any help

---

### Post by Jhinta on 2013-04-10
got it to work .
seem it needs a firmware for its usb chipset ( usb id will be swap correctly then)
 its a cypress fx2 chip ( download the mac driver and find eyetvsatfree.hex
if you have that install fxload

lsusb to fill in adress of usb -->xxx/xxx
sudo fxload  -t fx2 -I ./eyetvsatfree.hex -D /dev/bus/usb/xxx/xxx
then you will have tunner . now only create a correct driver for it and udev

[ 3907.526525] usb 3-4: new high-speed USB device number 28 using xhci_hcd
[ 3907.542721] usb 3-4: New USB device found, idVendor=0fd9, idProduct=003c
[ 3907.542727] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 4165.172469] usb 3-4: USB disconnect, device number 28
[ 4166.934844] usb 3-4: new high-speed USB device number 29 using xhci_hcd
[ 4166.951998] usb 3-4: New USB device found, idVendor=0fd9, idProduct=003b
[ 4166.952005] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4166.952008] usb 3-4: Product: EyeTV Sat Free
[ 4166.952011] usb 3-4: Manufacturer: Elgato Systems GmbH
[ 4166.952014] usb 3-4: SerialNumber: 42949017
[ 4166.952381] usb 3-4: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 4166.952389] usb 3-4: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 4166.952395] usb 3-4: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes

---

