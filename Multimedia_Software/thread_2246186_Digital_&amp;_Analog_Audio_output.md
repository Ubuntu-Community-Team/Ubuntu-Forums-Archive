---
title: "Digital &amp; Analog Audio output"
date: 2014-09-29
forum: Multimedia Software
---

### Post by Thumpxr on 2014-09-29
Hey,
I have a ASRock Z87 fatility killer mainboard with the onboard soundcard and have the 14.04 64Bit version of ubuntu.

My problem is that i can not select the digital (connected to my 5.1 system via Toslink) and the analog (connected to my headset, 3.5mm jack) at the same time for different programs.
Back in windows i could easily select either the one or the other.

*aplay -l*:
```
[COLOR=#000000][FONT=Courier New]APLAY**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1150 Digital [ALC1150 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]card 0: Intel [HDA Intel], device 1: ALC1150 Analog [ALC1150 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0[/FONT][/COLOR]
```


I already tried to add 
```
pacmd >> load-module module-alsa-sink device=hw:0,1
```
But got an error.

---

### Post by Vladlenin5000 on 2014-09-30
Could you use them simultaneously in Windows? I don't think so...

---

