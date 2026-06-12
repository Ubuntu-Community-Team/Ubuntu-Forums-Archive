---
title: "[SOLVED] No digital audio on MSI media live"
date: 2008-03-06
forum: Mythbuntu
---

### Post by Juppers on 2008-03-06
How do I enable the digital interface for playback? I can't find it at all in the mixer playback settings and I haven't found a similar issue through search engines at all. Any ideas?


```
[~]:cat /proc/asound/pcm 
00-02: ALC883 Analog : ALC883 Analog : capture 2
00-01: ALC883 Digital : ALC883 Digital : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

[~]: aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[~]: aplay -L
default:CARD=NVidia
    HDA NVidia, ALC883 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

---

### Post by newlinux on 2008-03-06
[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF)
may help. First, make sure it is unmuted using the
```

alsamixer 

```
command (use the TAB key to make sure you are viewing ALL playback devices).

---

### Post by Juppers on 2008-03-06
It isn't there to unmute. It is being listed as a capture device only.

---

### Post by Juppers on 2008-03-06
Solved, found the answer in product reviews on Newegg. 

> Resolved the HD audio not allowing digital output configuration in newer bios. Needed to disable the 8ch Audio in the bios

---

### Post by jacw on 2008-03-20
could you be more specific? I can't find the quote.

---

