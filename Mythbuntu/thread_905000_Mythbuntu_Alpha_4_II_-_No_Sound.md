---
title: "Mythbuntu Alpha 4 II - No Sound"
date: 2008-08-29
forum: Mythbuntu
---

### Post by DemonBob on 2008-08-29
I did a upgrade from 8.04 to 8.10 a little while ago. Sound was working find in 8.04 with mythtv, but not with 8.10. I know this is a Alpha, and i expect problems, just figured i'd through this out thier before i go back to 8.04 

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L

```
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

lspci -vnn

```
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Giga-byte Technology Device [1458:a002]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at e9300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Both Live TV, and any new recorded files do not play sound. 

If i open up a pre-upgrade recording with VLC sound works. Any new recorded programs, sound does not. 

I belive this may be a mythtv issue, but any help tracking this down would be apperiated.

---

### Post by DemonBob on 2008-08-29
Also no sound from VLC if i select capture device->PVR

---

