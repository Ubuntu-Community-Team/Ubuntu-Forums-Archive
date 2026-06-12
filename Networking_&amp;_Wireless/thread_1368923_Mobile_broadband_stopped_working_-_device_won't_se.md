---
title: "Mobile broadband stopped working - device won't settle?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by JohnTheLutheran on 2009-12-31
I'm running UNR Karmic on an Acer AspireOne. I've been using a ZTE MF628+ mobile broadband dongle from 3, and had this working fine using usb_modeswitch. 

However, following an update of my system just before Christmas, the dongle is no longer working. It looks like the problem relates to what happens when the dongle is plugged in, rather than being anything to do with usb_modeswitch. 

When plugged in, I get the following output from dmesg: 
```
[  417.736212] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  417.882947] usb 1-2: configuration #1 chosen from 1 choice
[  417.905150] scsi3 : SCSI emulation for USB Mass Storage devices
[  417.918977] usb-storage: device found at 4
[  417.918984] usb-storage: waiting for device to settle before scanning
```
There is no further dmesg output relating to the dongle after that. The dongle is reported correctly if I run lsusb: 
```
Bus 001 Device 005: ID 19d2:2000 ONDA Communication S.p.A. 
```
However, if I run usb_modeswitch then I get the following: 
```
~$ sudo usb_modeswitch 
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 006 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE CDMA Technologies MSM
  Serial No.: not provided
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.
```
The dongle still works on this netbook if I boot into a live USB install I have of Karmic. I get the following output (from /var/log/messages):
```
Dec 31 12:31:53 ubuntu kernel: [  137.816193] usb 1-2: new high speed USB device using ehci_hcd and address 4
Dec 31 12:31:53 ubuntu kernel: [  137.960914] usb 1-2: configuration #1 chosen from 1 choice
Dec 31 12:31:53 ubuntu kernel: [  137.977164] scsi3 : SCSI emulation for USB Mass Storage devices
Dec 31 12:31:59 ubuntu kernel: [  143.344572] usb 1-2: USB disconnect, address 4
Dec 31 12:32:05 ubuntu kernel: [  149.104102] usb 1-2: new high speed USB device using ehci_hcd and address 5
Dec 31 12:32:05 ubuntu kernel: [  149.250525] usb 1-2: configuration #1 chosen from 1 choice
Dec 31 12:32:05 ubuntu kernel: [  149.263978] scsi4 : SCSI emulation for USB Mass Storage devices
Dec 31 12:32:05 ubuntu kernel: [  149.305774] usbcore: registered new interface driver usbserial
Dec 31 12:32:05 ubuntu kernel: [  149.305822] USB Serial support registered for generic
Dec 31 12:32:05 ubuntu kernel: [  149.305930] usbcore: registered new interface driver usbserial_generic
Dec 31 12:32:05 ubuntu kernel: [  149.305939] usbserial: USB Serial Driver core
Dec 31 12:32:05 ubuntu kernel: [  149.322169] USB Serial support registered for GSM modem (1-port)
Dec 31 12:32:05 ubuntu kernel: [  149.322324] option 1-2:1.0: GSM modem (1-port) converter detected
Dec 31 12:32:05 ubuntu kernel: [  149.322532] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Dec 31 12:32:05 ubuntu kernel: [  149.322594] option 1-2:1.1: GSM modem (1-port) converter detected
Dec 31 12:32:05 ubuntu kernel: [  149.322786] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Dec 31 12:32:05 ubuntu kernel: [  149.322857] option 1-2:1.3: GSM modem (1-port) converter detected
Dec 31 12:32:05 ubuntu kernel: [  149.323080] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Dec 31 12:32:05 ubuntu kernel: [  149.323123] usbcore: registered new interface driver option
Dec 31 12:32:05 ubuntu kernel: [  149.323130] option: v0.7.2:USB Driver for GSM modems
Dec 31 12:32:10 ubuntu kernel: [  154.267670] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 31 12:32:10 ubuntu kernel: [  154.270668] scsi 4:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Dec 31 12:32:10 ubuntu kernel: [  154.272664] sd 4:0:0:0: Attached scsi generic sg2 type 0
Dec 31 12:32:10 ubuntu kernel: [  154.297762] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Dec 31 12:32:10 ubuntu kernel: [  154.313101] sr0: scsi-1 drive
Dec 31 12:32:10 ubuntu kernel: [  154.313119] Uniform CD-ROM driver Revision: 3.20
Dec 31 12:32:10 ubuntu kernel: [  154.313591] sr 4:0:0:1: Attached scsi generic sg3 type 5
```
Any suggestions gratefully received!

---

### Post by GeorgeVita on 2009-12-31
Hi **JohnTheLutheran**, please try something easy:

- remove any existing 'mobile broadband' connection (from nm icon)
- boot without modem
- do not use usb-modeswitch
- after appear of Zero-CD drive (icon or check dmesg) eject it
- wait some seconds and click on nm icon to see if any 'new broadband connection' exists

Regards,
George

---

### Post by JohnTheLutheran on 2009-12-31
Thanks! Worked like a charm. 

Is there an easy way to make the zero-cd ejection automatic?

---

### Post by GeorgeVita on 2009-12-31
Yes, creating a udev rule:

> **Sergiu Bivol said:**
> It's been a while since the usb_modeswitch rules for udev do not work anymore in Karmic. Even running usb_modeswitch from the console gives errors most times ("could not claim interface").
The good news is that this program is not needed anymore. Just create a new file *ZTE.rules* under */etc/udev/rules.d*, containing: ```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```
Delete any usb_modeswitch rules you have.
This solves the "switching" part.

This means: ```
gksudo gedit /etc/udev/rules.d/90-ejZTE.rule
```
and copy inside: ```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```

Regards,
George

---

### Post by JohnTheLutheran on 2009-12-31
Superb! Thanks for this.

---

