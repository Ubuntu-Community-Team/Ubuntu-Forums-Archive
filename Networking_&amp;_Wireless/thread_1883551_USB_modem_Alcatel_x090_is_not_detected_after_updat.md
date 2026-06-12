---
title: "USB modem Alcatel x090 is not detected after updating 11.10.."
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by Atul88 on 2011-11-19
My USB modem Alcatel x090 stops working after upgrading to 11.10 from 11.04. 

lsusb command results as :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 007: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 008: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 009: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 010: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 002 Device 006: ID 1bbb:0000 T & A Mobile Phones 

And output of dmesg | grep tty

[ 5233.564515] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[ 5233.564785] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[ 5233.565602] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2

So i think it is switched to modem mode but nm is not able to recognize this and sakis3g is not working too..


Pls help....  M i missing somthing ?

---

