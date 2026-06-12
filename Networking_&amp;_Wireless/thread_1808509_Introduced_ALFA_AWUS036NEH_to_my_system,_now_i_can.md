---
title: "Introduced ALFA AWUS036NEH to my system, now i can't connect at all"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by Filmor on 2011-07-20
Just recently bought a ALFA AWUS036NEH usb dongle, everything was fine before i connected it for the first time, now i can't connect at all; it seems like both cards are active(onboard & usb dongle) both just disconnect the moment i attempt to connect to a wifi spot.

please help, i love ubuntu and want to make this work.

what can i do to fix this.

---

### Post by thefasterblueone on 2011-07-20
reboot computer and enter "BIOS", disable "onboard lan", should work then.

---

### Post by Filmor on 2011-07-20
I disabled onboard wifi on the bios now both cards are showing up as disabled, maybe i should update the firmware for the card?

---

### Post by wildmanne39 on 2011-07-20
> **Filmor said:**
> I disabled onboard wifi on the bios now both cards are showing up as disabled, maybe i should update the firmware for the card?Hi, you probably still need to install the driver for your usb card. Type this in a terminal
please
```
lsusb
```
```
sudo lshw -C network 
```
```
iwconfig
```
```
rfkill list All
```
and post the results here.
Thank you

---

