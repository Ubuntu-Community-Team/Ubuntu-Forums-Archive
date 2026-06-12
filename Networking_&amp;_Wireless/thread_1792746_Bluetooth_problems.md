---
title: "Bluetooth problems"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by sark_ on 2011-06-28
Hi, I'm new to Ubuntu and I think I'm having issues with the bluez daemon. Whenever I start the BLueman manager, a pompt comes up saying "Bluez daemon is not running, blueman-manager cannot continue." My bluetooth dongle is an IO Gear BGU421, which I've read is supposed to work out of the box in Ubuntu. When I put lsusb into a terminal, I get this back: 

$ lsusb
Bus 004 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 002: ID 06a3:0728 Saitek PLC 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So I assume the computer knows the adapter is there. I'm running 10.04 and to be honest I really have no idea what I'm doing, any help would be greatly appreciated. Thanks!

---

### Post by noletolucas on 2012-03-17
Same problem. Inspiron N4030, Ubuntu 10.04.

from lsusb:
```
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

---

