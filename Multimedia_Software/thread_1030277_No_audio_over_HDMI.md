---
title: "No audio over HDMI"
date: 2009-01-04
forum: Multimedia Software
---

### Post by primozho on 2009-01-04
I'm running Ubuntu 8.10 (Intrepid) kernel 2.6.27-9-generic GNOME 2.24.1 on Lenovo 3000 N500 notebook with Intel 4500MHD graphics.
My problem is no HDMI audio.
I've installed ALSA driver 1.0.18a, everything is checked ( IEC958 ) and maxed out in alsamixer, but still no audio over HDMI.
Here is my aplay -l
[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/PHP]
and aplay -L
[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
primoz@primoz-laptop:~$ aplay -L
default:CARD=Intel
    HDA Intel, CONEXANT Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
[/PHP]
If I swich device in System/Preferences/Sound to HDA Intel INTEL HDMI (ALSA) an hit Test, I get no audio.
Same with aplay -Dplughw:0,3 audiofile.wav

Any suggestions?

---

### Post by densou on 2009-01-05
> **primozho said:**
> Any suggestions?

not at all, it's a well-known issue with Intel stuff (mainly G35 and newer)

2.6.28 Kernel should have fixed but drivers are still stuck on development (Intel video 2.5.99)

note: it seemed it's not related to Alsa ;) 

[http://bugs.freedesktop.org/buglist.cgi?quicksearch=intel+hdmi](http://bugs.freedesktop.org/buglist.cgi?quicksearch=intel+hdmi)

---

