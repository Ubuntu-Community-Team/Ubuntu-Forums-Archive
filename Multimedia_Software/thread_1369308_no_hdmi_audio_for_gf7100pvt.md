---
title: "no hdmi audio for gf7100pvt"
date: 2009-12-31
forum: Multimedia Software
---

### Post by dh4 on 2009-12-31
I have a motherboard (ecs gf7100pvt-m3) with on-board audio/video.  I'm trying to connect via hdmi to a tv but i get no audio.  I am running ubuntu 9.10, alsa 1.0.21 kernel 2.6.31-16-generic.
It is a set up with the motherboard sending audio out through the dvi -> passive connector -> hdmi.
It works in windows so it is not a h/w issue.
The sound device gets recognized and the controls in alsamixer look sensible.
I have read many posts and followed many suggestions but still no sound over hdmi.  the sound does work
from the normal analog output.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

cat /sys/class/sound/hwC0D0/modelname
   6stack-dig-demo

I have tried many different models, no hdmi sound with any.

Help would be appreciated.

---

