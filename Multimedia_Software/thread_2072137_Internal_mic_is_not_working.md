---
title: "Internal mic is not working"
date: 2012-10-17
forum: Multimedia Software
---

### Post by yogix on 2012-10-17
Internal mic and headphone microphone both are not working in Samsung N100SP netbook installed with Edubuntu 12.04. The netbook has single port both for input and output. I've installed pulse audio volume control and could see microphone in Input Devices tab. Constant noise is heard when the recording is done using Sound recorder application.
Please help me in this.

Thanks in advance.:)

---

### Post by pqwoerituytrueiwoq on 2012-10-17
we need some system info
i assume you have tried all options in [FONT=Courier New]pavucontrol[/FONT]
```
lapci | grep Audio
aplay -l
arecord -l
```

---

### Post by yogix on 2012-10-18
yep, i have tried all the options in > pavucontrol.
Here's the output of the above commands,

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

