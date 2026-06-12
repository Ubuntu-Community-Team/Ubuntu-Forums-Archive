---
title: "Netgear WG111v3 works!!!"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by tonyps on 2009-08-15
Afternoon,

For those of you looking to get wireless working, I can recommend this one...After way too much reading, typing, modifying, building, reading, searching,,,,well, you get the idea...
I bought this one this morning, pluged it in and it works!! 
My hardware:
Tshiba A505D-SS6958
AMD Turion-X2/64
4GB RAM
500GB HD
ATI Radeon 3100
Built-in Ethernet:
SUCKS!!- 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
Works, first time, no issues- 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
 Realtek

Best of luck,
Tony ...

---

### Post by pytheas22 on 2009-08-15
So you didn't have to use ndiswrapper?  Which version of Ubuntu are you using?  Is your wireless network using WEP or WPA encryption?  What is the output with the WG111v3 plugged in of the command:
```

lsusb
```

I've been involved in many threads dealing with this card and I thought that there was no native Linux driver for it; maybe that's changed.  It also has never worked reliably for anyone using WPA, so I'd be especially interested if you've got it working with that, and it has run for several hours without crashing.

---

### Post by abhi.datt on 2009-08-28
Yep, this works perfectly on Jaunty Jackalope 9.04 (32 Bit)

Just plugin and wait for couple of seconds, blue ligt will glow. That's the time you should know its drivers are loaded, wait for few seconds more and you will see NetworkManger applet configuring it for you. This could not be easier
For others reference, here is my lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Notice Device 003 in line 2

Also attaching an image of my Network applet, that clearly shows my two network cards present, one inbuilt Dell's and other of Netgear

Cheers

---

### Post by pytheas22 on 2009-08-29
abhi.datt: thanks for the update.  I just realized I was thinking of the WPN111 having issues (which is apparently still the case), not the WG111v3...I was just confused.  Glad to hear the WG111v3 is problem-free in Jaunty.

---

### Post by TraceurJ on 2009-08-30
Does it support Packet injection?

---

### Post by TraceurJ on 2009-08-30
Does it?

---

### Post by pytheas22 on 2009-08-30
> Does it support Packet injection? 

It uses the rtl8187b driver, so [probably]("http://aircrack-ng.org/doku.php?id=rtl8187").

---

### Post by TraceurJ on 2009-08-30
Thanks a lot

---

