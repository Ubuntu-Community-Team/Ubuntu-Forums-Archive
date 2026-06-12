---
title: "spdif surround sound help"
date: 2010-05-28
forum: Multimedia Software
---

### Post by metalmaniac248 on 2010-05-28
hi there

i am trying to get digital surround to work on ubuntu 10.04 via spdif out

i looked at this page [http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")

and tryed this command ```
aplay -D iec958:CARD=NVidia,DEV=0 Norrlanda.wav
```

to test if surround sound was working (the Norrlanda.wav file is a 5.1 DTS file) i did get the sound out of my speakers and my receiver said that it was receiving DTS sound however, it was only receving the DTS sound in 2.1 not 5.1

and BTW in my sound prefences (system > preferences > sound) i have the hardware set to Digital stereo out as their is no option for digital surround out

can anyone help?

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by wwbart on 2010-06-02
I have the same problem. I have posted what all was asked for

# uname -a
Linux Hostname 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21

# head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC883

---

