---
title: "Freepulse Wireless Headphones"
date: 2009-01-25
forum: Multimedia Software
---

### Post by fuzzybear3965 on 2009-01-25
Okay so I want to connect my Freepulse Wireless Headphones to my PC sans the use of the 1/8" dongle.  Is it possible to pair my headphones with my PC on Ubuntu 8.10?  Because it would be really nice to listen to music wirelessly around the house without having to use that dangly dongle all the time.

---

### Post by blackdalek on 2009-04-13
I want to know the answer to this too because my dongle that comes with the FreePulse headphones is broken.

---

### Post by debb1046 on 2009-05-02
I have it working in Jaunty. The pairing was a bit more complicated than with my other headsets. The following steps did it for me:

put the headset in pairing mode by pressing and holding the power switch until the LED flashes blue/red (takes some time)

click on the bluetooth applet (Setup new device). Used 0000 as pin. 

With the LED still flashing, found the bluetooth address with ```
hcitool scan
```With the LED still flashing, loaded the device into pulseaudio:
```
pactl load-module module-bluetooth-device address=00:0D:44:85:BD:DB profile=a2dp
```where the address is the one previously found by hcitool. The LED on the headphone changed to soild blue at this point.

used pulseaudio volume control to shift playback to the headset

I am using updated bluez and pulseaudio packages from:
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/bmillemathias/ppa/ubuntu](http://ppa.launchpad.net/bmillemathias/ppa/ubuntu) jaunty main

Good luck,
Reiner

---

### Post by fuzzybear3965 on 2009-05-04
john@john:~$ hcitool scan
Device is not available: No such device

Now what do I do?  And can I get the keys for those PPAs?  Software Sources rejects them.

---

