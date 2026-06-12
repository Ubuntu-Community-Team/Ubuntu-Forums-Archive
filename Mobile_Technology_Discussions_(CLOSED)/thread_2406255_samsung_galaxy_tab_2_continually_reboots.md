---
title: "samsung galaxy tab 2 continually reboots"
date: 2018-11-18
forum: Mobile Technology Discussions (CLOSED)
---

### Post by pdcooper on 2018-11-18
so the tablet continually reboots at approx 1 minute intervals . 
booting into recovery mode and doing fatory reset says it is wiping everything but then rebooting the , tablet is just as it was. 
If Im quick i can get into the GUI reset menu , but that changes nothing. 

As the alternative is to put it in the bin, i want to have a play with Heimdall and flashing it with something 

heres the relevant ( I think) output. 

Am i wasting my time and i should just hit it with a hammer and put it in a skip ?  

```

dmesg 
  386.766465] usb 1-6: new high-speed USB device number 6 using ehci-pci
[  386.923560] usb 1-6: unable to get BOS descriptor
[  386.924430] usb 1-6: New USB device found, idVendor=0451, idProduct=d00f
[  386.924435] usb 1-6: New USB device strings: Mfr=33, Product=37, SerialNumber=0
[  386.924439] usb 1-6: Product: OMAP4430
[  386.924443] usb 1-6: Manufacturer: Texas Instruments
[  389.925449] usb 1-6: USB disconnect, device number 6
[  528.838012] usb 1-6: new high-speed USB device number 7 using ehci-pci
[  528.995060] usb 1-6: unable to get BOS descriptor
[  528.995930] usb 1-6: New USB device found, idVendor=0451, idProduct=d00f
[  528.995935] usb 1-6: New USB device strings: Mfr=33, Product=37, SerialNumber=0
[  528.995939] usb 1-6: Product: OMAP4430
[  528.995943] usb 1-6: Manufacturer: Texas Instruments
[  531.996934] usb 1-6: USB disconnect, device number 7
[ 1011.716623] usb 1-6: new high-speed USB device number 8 using ehci-pci
[ 1011.873814] usb 1-6: New USB device found, idVendor=04e8, idProduct=6860
[ 1011.873821] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1011.873825] usb 1-6: Product: GT-P5110
[ 1011.873829] usb 1-6: Manufacturer: samsung
[ 1011.873833] usb 1-6: SerialNumber: c1607bf070dccaf




me@mine:~$ lsusb
Bus 001 Device 009: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 005: ID 0ac8:3450 Z-Star Microelectronics Corp. 
Bus 001 Device 004: ID 03f0:0c17 Hewlett-Packard LaserJet 1010
Bus 001 Device 003: ID 1d57:0005 Xenta Wireless Receiver (Keyboard and Mouse)
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


me@mine:~$ mtp-detect
libmtp version: 1.1.13


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 1, dev 13
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
inep: usb_get_endpoint_status(): Resource temporarily unavailable
outep: usb_get_endpoint_status(): Device or resource busy


me@mine:~$ mtp-detect
libmtp version: 1.1.13


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 1, dev 13
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
inep: usb_get_endpoint_status(): No such device
outep: usb_get_endpoint_status(): No such device
libusb_open() failed!: No such file or directory
LIBMTP PANIC: Could not init USB on second attempt
Unable to open raw device 0
OK.

```

---

