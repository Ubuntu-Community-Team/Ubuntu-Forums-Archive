---
title: "Tp-wn321g v4 - No scan results"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Vaquero303 on 2011-06-02
Well guys, I believe that the title is self explanatory.

I use Ubuntu 10.04 and Ive just bought an USB WIRELESS ADAPTER: **Tp-wn321g v4.1.**
I have no problems until y try to scan for networks via "iwlist wlan0 scan" or "Wifi Radar".
"No scan results" says.

I tried ifconfig, iwconfig, lsusb, lsmod and: device is detected, device is recogniced, chipset ra2500 recogniced, usb version ok, modules up.

I also tried **sudo iwlist wlan0 scan** with no results either.

The pc isnt a laptop so, It doesnt have "Wifi Interruptor".

The driver I use is **rt2800usb**.

Ive tried in windows Xp and the adapter detects several networks at reach.

Im a newbie In linux world and Im running out of ideas.. 
Any suggestions?
Thanks in advance,
Martin

P-d: Excuse my english! :P

---

### Post by josephmills on 2011-06-02
try ```
iwlist scan 
``` what do you get

---

### Post by Vaquero303 on 2011-06-02
Thanks for answering so fast.
Ive tried, and get:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

``` 

The same result...
This is driving me mad! xD

---

### Post by josephmills on 2011-06-02
plug in the usb and then let us see a ```
lsusb
``` and a ```
lsmod | grep rt 
``` thanks

---

### Post by Vaquero303 on 2011-06-02
lsusb:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


lsmod | grep rt:
```

rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```

---

### Post by Vaquero303 on 2011-06-05
Guys, in GNOME Live the adapter works fine! :mad:

---

