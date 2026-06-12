---
title: "Avermedia Aver3d Volar Mini A836"
date: 2012-08-28
forum: Multimedia Software
---

### Post by polballesta on 2012-08-28
Hello everybody, my first post here.

I'm trying to install my tv tunner Aver3d Volar Mini A836 in Ubuntu 12.04.

lsusb:

**Bus 001 Device 011: ID 07ca:a836 AVerMedia Technologies, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 005: ID 0461:0010 Primax Electronics, Ltd 
Bus 002 Device 003: ID 192f:0916 Avago Technologies, Pte.


dmesg | grep -i dvb

don't get me any results.


I try to install in different ways with no succes. I'm trying to leave windows for ubuntu, but it's the only thing that isn't working well in ubuntu.

Thank you in advance for your help and sorry for my bad english.I notice that my knowledge in ubuntu is basic, I'm still learning.

---

### Post by 2F4U on 2012-08-29
Seems as if you need to find the appropriate firmware for this device, since it is not included. Else the device would show up.

---

### Post by polballesta on 2012-08-29
> **2F4U said:**
> Seems as if you need to find the appropriate firmware for this device, since it is not included. Else the device would show up.

Yes, I know, but I can't find it, or I didn't know where to find it...

---

### Post by polballesta on 2012-09-01
it seems that i don't have luck... Nobody can help me?

---

### Post by BicyclerBoy on 2012-09-02
Your model is not listed here:
[http://linuxtv.org/wiki/index.php/AVerMedia](http://linuxtv.org/wiki/index.php/AVerMedia)

There is **no** vendor supplied linux driver for A836.

If a tuner is not listed as working on LinuxTV.org then stay well clear..

---

### Post by polballesta on 2012-09-03
> **BicyclerBoy said:**
> Your model is not listed here:
[http://linuxtv.org/wiki/index.php/AVerMedia](http://linuxtv.org/wiki/index.php/AVerMedia)

There is **no** vendor supplied linux driver for A836.

If a tuner is not listed as working on LinuxTV.org then stay well clear..

Ok, thank you. I'll wait to see if someone gets a proper firmware

---

### Post by BicyclerBoy on 2012-09-05
The firmware (if there is any) is the easier bit..it could be extracted from warm dual boot machine (with windows) or from the windows driver itself.

The problem is the hardware has to be reverse engineered so a hardware driver can be written.
If the h/w is similar to any existing model then that could be less of a nightmare.

So there may never be a linux driver for this device.

---

