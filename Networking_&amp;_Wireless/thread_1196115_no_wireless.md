---
title: "no wireless"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Zom-b on 2009-06-24
I have been trying to get my wireless to work for sometime now looking all over for any sort of guide or howto, and so far none of the ones I have tried have worked the laptop I'm using is a Compaq Presario V2000

I have tried reinstalling ndiswrapper and some other drivers but to no avail, sometimes the wifi button lights up but I can't find any networks when I scan, when I click on network mananger it shows the wired connection I have plugged in right now, but for wireless connection it doesn't list anything

this is what I have for lshw -C network....
```

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:cc:7a:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.15.102 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:13:f0:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

---

### Post by drrdf2 on 2009-06-24
Try the procedure here: 


[http://ubuntuforums.org/showthread.php?t=1118187](http://ubuntuforums.org/showthread.php?t=1118187)

---

### Post by Zom-b on 2009-06-24
I tried that but it didn't seem to do anything, I am still having the same problem

---

### Post by drrdf2 on 2009-06-24
It may be that your wireless card is just not compatible with Ubuntu. 

Have you looked at the compatibility list? There is a link on the first forum page sticky entries.

---

### Post by Ayuthia on 2009-06-24
What does:
```
dmesg|grep b43
```show?  It looks like your computer is trying to use the b43 module.  Is that what you are trying to use or is it NDISwrapper?

---

### Post by Zom-b on 2009-06-24
> **drrdf2 said:**
> It may be that your wireless card is just not compatible with Ubuntu. 

Have you looked at the compatibility list? There is a link on the first forum page sticky entries.

yeah it is on the compatibility list I made sure to check

---

### Post by Zom-b on 2009-06-24
> **Ayuthia said:**
> What does:
```
dmesg|grep b43
```show?  It looks like your computer is trying to use the b43 module.  Is that what you are trying to use or is it NDISwrapper?

when I type dmesg | grep b43 the output is...
```

zomb@zomb-laptop2:~$ dmesg | grep b43
[   27.987461] b43-phy0: Broadcom 4318 WLAN found
[   28.030163] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   28.030193] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   34.729967] b43-phy1: Broadcom 4318 WLAN found
[   34.770938] b43-phy1 debug: Found PHY: Analog 3, Type 2, Revision 7
[   34.770965] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   71.916994] input: b43-phy1 as /devices/virtual/input/input11
[   36.231653] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   37.070389] b43-phy1 debug: Chip initialized
[   37.070885] b43-phy1 debug: 32-bit DMA initialized
[   37.090066] Registered led device: b43-phy1:radio
[   37.090114] b43-phy1 debug: Wireless interface started
[   37.136501] b43-phy1: Radio hardware status changed to DISABLED
[   37.137713] b43-phy1 debug: Adding Interface type 2

```

---

