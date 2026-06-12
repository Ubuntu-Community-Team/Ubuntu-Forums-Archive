---
title: "Ralink 802.11 n WLAN usb"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by cornflayke on 2010-12-25
Hey, 

I'm a new user of Ubuntu and I think I need some help but let me mention before that I got this up working on a Debian system.

My current kernel version is $ uname -r
2.6.32-27-generic

The problem is that my wlan card is not working any more such that my system freezes every time I enable networking with the hardware switch on my laptop. 
Therefore I bought a USB - WLAN stick and try to get this working.

Network Manager has the option "enable wireless" greyed out if I disable the hardware switch.
If I enable the hardware switch and remove the module of my wlan CARD before (modprobe -r iwl3945) it says "wireless disconnected" for all networks.

My lsmod output with "rt" grepped looks like:

```

rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
rt2870sta             461811  0 
led_class               2864  2 rt2x00lib,sdhci
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```I think at the moment that all I need would be the firmware-ralink package (and of course blacklist iwl3945 and rt2800) as the Ralink software appears to be:
$ lsusb | grep Ralink:
```

Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 

```But "sudo apt-get install firmware ralink" just gives me a:
E: Package firmware-ralink has no installation candidate

But I can't figure out which sources I need for this.

Thanks for any help in advance.

---

### Post by cornflayke on 2010-12-26
Hey, 

I solved my problem,
for those of you which are interested in the solution:
**I installed the rt73 source and commom packages.**
After that everything went fine.

---

