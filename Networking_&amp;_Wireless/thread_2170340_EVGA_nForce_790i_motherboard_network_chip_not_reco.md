---
title: "EVGA nForce 790i motherboard network chip not recognized"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by H4ST3 on 2013-08-25
I am booting into a live usb instance of ubuntu 13.04. Unfortunately, I can't seem to get the system to recognize and activate either of the embbeded chips on the nVida 790i FTW motherboard. '

lshw -C network returns nothing.

ifconfig only returns information for the loopback lo

Any assistance is greatly appreciated.

Thanks in advance

---

### Post by chili555 on 2013-08-25
How about:```
lsusb
lspci -nn
```Thanks.

---

### Post by H4ST3 on 2013-08-25
lusb
Bus 001 Device 002: ID 1307.0165 Transcend Information, Inc. 2Gb/4GB flash drive
Bus 001 Device 001: ID xxxx.xxxx Pixart imaging, Inc. Optical mouse
Bus 001 Device 002: ID xxxx.xxxx Lnux Foundation 2.0 Root hub
Bus 001 Device 001: ID xxxx.xxxx Linux Foundation 1.0 Root hub

lspci 
00.00.0 Host bridge [0660]: NVIDIA Corporation Device [10de.0892] (rev b1)
00.00.1 RAM memory [0500]:  NVIDIA Corporation Device [10de.08808] (rev a1) 
00.00.2 RAM memory [0500]:  NVIDIA Corporation Device [10de.08809] (rev a1) 
00.00.3 RAM memory [0500]:  NVIDIA Corporation Device [10de.08810] (rev a1) 
00.00.4 RAM memory [0500]:  NVIDIA Corporation Device [10de.08811] (rev a1) 
00.00.5 RAM memory [0500]:  NVIDIA Corporation Device [10de.08812] (rev a1) 
00.00.6 RAM memory [0500]:  NVIDIA Corporation Device [10de.08813] (rev a1) 
00.00.7 RAM memory [0500]:  NVIDIA Corporation Device [10de.08814] (rev a1) 
00.01.1 RAM memory [0500]:  NVIDIA Corporation Device [10de.08815] (rev a1) 
...
00.02.0 PCI bridge [0664]: NVIDIA Corporation Device [xxxx.xxxxx]
00.04.0 PCI bridge [0664]: NVIDIA Corporation Device [xxxx.xxxxx]
00.02.0 RAM memory [xxx]: NVIDIA Corporation MCP55 memory controller [xxxx.xxxxx] (rev a2)
...

it goes on to list SATA & IDE controllers, audio controllers, VGA compatible controllers, etc.

but it doesn't list anything for the network controller. I don't even know what chipset is in this thing.

---

### Post by chili555 on 2013-08-25
I'm sorry, I don't see anything resembling a networking device, either wired or wireless. Are you certain the mobo comes with one by default? Is there any setting in the BIOS to enable them?

---

