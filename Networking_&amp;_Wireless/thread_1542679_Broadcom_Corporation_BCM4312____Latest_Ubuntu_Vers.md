---
title: "Broadcom Corporation BCM4312  //  Latest Ubuntu Version  //  HP 67352 Notebook"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by Swanny2010 on 2010-07-30
My wireless isnt working on my HP 6735s Notebook.
Theres no drivers in the driver manager nor does it find my network.
The wireless indicator on my laptop also shows my wireless is turned off even when i press the button to turn it on.

lspci:

michael@ubuntu:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) 
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) 
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10) 
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev ff) 
michael@ubuntu:~$ 

$ lsusb:

*-network 
description: Ethernet interface 
product: Marvell Technology Group Ltd. 
vendor: Marvell Technology Group Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 10 
serial: 00:24:81:4b:39:d5 
width: 64 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes 
resources: irq:28 memory:53100000-53103fff ioport:3000(size=256) 
*-network DISABLED 
description: Wireless interface 
physical id: 1 
logical name: wlan0 
serial: 00:21:00:ba:ff:f0 
capabilities: ethernet physical wireless 
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
michael@ubuntu:~$


Any help ?

---

### Post by Swanny2010 on 2010-07-31
Ok so on ubuntu 9.4 it does works but on 10.0 & 9.10 it doesnt ?

---

### Post by Swanny2010 on 2010-07-31
any help?

---

### Post by DEVIL DOG on 2010-07-31
In 10.04 go to System>Administration>Hardware Drivers and activate the driver.  You must be wired to the internet connection to do this.  I have the same wireless hardware.

---

