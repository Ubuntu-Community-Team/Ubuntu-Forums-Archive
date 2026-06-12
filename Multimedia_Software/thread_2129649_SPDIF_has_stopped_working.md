---
title: "S/PDIF has stopped working"
date: 2013-03-26
forum: Multimedia Software
---

### Post by ronsonk on 2013-03-26
Hi,

S/PDIF has been working for me for several years now, under both ALSA and Pulseaudio.  Until now. It has stopped working after using a set of USB headphones.

I plugged in a set of USB headphones based on a Plantronics chipset, selected the headphone hardware in in Sound Settings and completed a VOIP call. I unplugged the headset and ensured that my digital output was selected (S/PDIF).  However, I have no signal to the receiver now.  This is despite numerous reboots, updates etc.

Plugging the headset back in and selecting the headset hardware works. 

My S/PDIF output is direct from the motherboard and is (according to aplay -l):

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any help would be much appreciated. Thanks!

---

### Post by ronsonk on 2013-04-03
I've also check in Alsamixer - S/PDIF is not muted.

---

