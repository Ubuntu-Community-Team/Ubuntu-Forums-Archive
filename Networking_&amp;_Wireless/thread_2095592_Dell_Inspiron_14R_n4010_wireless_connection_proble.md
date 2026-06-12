---
title: "Dell Inspiron 14R n4010 wireless connection problem"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by geekking on 2012-12-17
I've recently installed ubuntu 12.04 in my laptop, i'd windows 7 and i totally erased all the system, i changed to ubuntu and the ethernet connection works fine but it seems like i don't have any driver for my wireless connection and i cant find it. Please Help

---

### Post by geekking on 2012-12-17
My mistake, ubuntu 12.10

---

### Post by chili555 on 2012-12-17
Please tell us what wireless card you have. Open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by N00b-un-2 on 2012-12-17
please post the output of
```
lspci -nn
```

---

### Post by geekking on 2012-12-17
lspci -nn | grep 0280 

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)

---

### Post by chili555 on 2012-12-17
Your wireless should work just fine. Please let us see:```
rfkill list all
```Thanks.

---

### Post by geekking on 2012-12-17
rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2012-12-17
> **geekking said:**
> rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]That suggests that the switch or key combination has the wireless switched off. Can you please switch it?

---

### Post by geekking on 2012-12-17
Ready. Yeah already solved, the most stupid thing. I thought in this by the beginning of my problem, but i dont know. Thanks

---

### Post by chili555 on 2012-12-17
Please use thread tools at the top to mark Solved. Glad it's working.

---

