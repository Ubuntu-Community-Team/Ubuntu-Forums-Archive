---
title: "No capture / microphone, AMD 64 NVidia"
date: 2008-09-13
forum: Multimedia Software
---

### Post by Duanebuntu on 2008-09-13
Thanks in advance for any replies.

Problem: I can't seem to capture any audio via external microphone or from my sound card. I have used alsamixer to unmute and enable all microphone devices and capture devices.

My system information:
OS: Ubuntu 8.04 (hardy)
Gnome version: 2.22.3 (Ubuntu 2008-07-09)
Kernal: 2.6.24-21-generic (#1 SMP Mon Aug 25 16:57:51 UTC 2008)
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Sound device: NVIDIA GeForce 6200 LE
NVIDIA graphic driver kernal module: NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008

One line from $ lspci
```
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```

$ arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

$ arecord -L
```
default:CARD=NVidia
    HDA NVidia, AD198x Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

Again, any help is much appreciated!

---

