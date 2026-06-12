---
title: "Wireless Networking"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by Walruin on 2011-05-13
Okay, I am having error trying to connect to wireless network.

When I installed the wubi, it installed just fine with no errors. (When it starts it gives error that I dont know, also I dont see system > adminsitartion tab)
Now that I open the tab that should show wireless networks, it doesnt show up! What am I doing wrong? Is there anyway I could get the wireless network to work?

Modem and Network: Wireless N ADSL2 & Modem Router TD-W8960N
Help appreciated, urgent

EDIT: b43 didnt help.

---

### Post by Walruin on 2011-05-13
Kinda Bump
I really need this

---

### Post by walt.smith1960 on 2011-05-13
I wonder if the errors you're getting are related to the wireless adapter?  Getting errors is seldom a good thing.  What is returned when you open a terminal and type "lspci" for internal adapters or "lsusb" for usb adapters? You mentioned b43. Do you know you have a Broadcom based adapter?

---

### Post by Walruin on 2011-05-14
LSPCI:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

LSUSB
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c50c Logitech, Inc. Cordless Desktop S510
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1370:2168 Swissbit 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Walruin on 2011-05-14
edited.

---

### Post by garvinrick4 on 2011-05-14
> This solution fixed this problem on my Dell Inspiron 1545 with a  Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller:  Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)) From thread:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Walruin on 2011-05-14
But I get no errors O_O

EDIT: I dont see the "Administration" in System > administration (theres no such thing called administration in system O.O) How to fix this?

---

### Post by Walruin on 2011-05-14
Kinda bump

---

### Post by Walruin on 2011-05-14
its pretty urgent

---

### Post by garvinrick4 on 2011-05-14
> **Walruin said:**
> But I get no errors O_O

EDIT: I dont see the "Administration" in System > administration (theres no such thing called administration in system O.O) How to fix this?
System drop down menu in upper left of 10.10 will say Preferences or Administration.
In 11.04 unity Windows key/A type in synaptic and click on it. Follow instructions from
link.

---

### Post by Walruin on 2011-05-16
Still having this problem omg, your solution didnt work O_O

---

