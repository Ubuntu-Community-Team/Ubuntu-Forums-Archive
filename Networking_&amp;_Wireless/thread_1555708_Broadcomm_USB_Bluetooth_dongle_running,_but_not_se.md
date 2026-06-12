---
title: "Broadcomm USB Bluetooth dongle running, but not seeing headset or Blackberry"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Paulzy on 2010-08-18
FIRSTLY:
**Ubuntu Jaunty 9.04 /kernel 2.6.28-19**

**[PJCI] pauljc:** lsusb
Bus 001 Device 007: ID 03f0:0f07 Hewlett-Packard 
Bus 001 Device 005: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 046d:c225 Logitech, Inc. 
Bus 002 Device 005: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[PJCI] pauljc: **hciconfig
hci0:	Type: USB
	BD Address: 00:02:72:A2:47:27 ACL MTU: 1021:7 SCO MTU: 64:1
	UP RUNNING 
	RX bytes:175 acl:0 sco:0 events:21 errors:0
	TX bytes:331 acl:0 sco:0 commands:21 errors:0

OK Ubuntu sees the deviuce, and I have it set to only show the Bluetooth icon if the adapter is present. However, when I press the pairng mode on my Sony DR-BT101 headset or Blackberry 9700 and then select Setup new device from the Bluetooth applte, the screen doesn't show any of teh devices.

As this is the first time I *(I did it once under 8.04/8.10 but found out that Bluetooth was officially supported for Jaunty, or so I read)* am I doing this right? Have I missed something?

---

