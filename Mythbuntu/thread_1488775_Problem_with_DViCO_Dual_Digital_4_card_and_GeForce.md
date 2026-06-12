---
title: "Problem with DViCO_Dual_Digital_4 card and GeForce FX5600 card"
date: 2010-05-20
forum: Mythbuntu
---

### Post by Suncoaster on 2010-05-20
I installed Mythbuntu 10.04 recently and everything worked using the Dvico dual digital 4 card and onboard graphics.  The picture was not wonderful so I obtained a GeForce FX5600 card and installed that and now nothing works. :confused: The command "dmesg | grep IR-rec" returns nothing and the lsusb command returns
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
so it would appear the dvb card is not being loaded.  I remember there being a hardware driver being loaded for the dvb card before I loaded the hardware driver for the video card, but now it has vanished.

Can I load both a driver for the dvb card as well as one for the video card.  Any help would be appreciated.

---

