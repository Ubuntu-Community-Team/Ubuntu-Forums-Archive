---
title: "Audio sounds like the Borg"
date: 2010-10-04
forum: Multimedia Software
---

### Post by Amorget on 2010-10-04
I have been running a happy Mythbuntu 10.04 setup for awhile now.  The other day I went to watch and video and the sound was all messed up.  It sort of sounds like the way the Borg talk.

I have uploaded a video to YouTube:

[http://www.youtube.com/watch?v=so8oRzlMdO8](http://www.youtube.com/watch?v=so8oRzlMdO8)

I upgrade my ASLA to 1.0.23 using the upgrade scripts.

Output of aplay:
```
amorget@mediacenterpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
amorget@mediacenterpc:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

Anyone have any ideas?

Thanks

---

### Post by Amorget on 2010-10-08
Any ideas?

---

### Post by Amorget on 2010-10-12
I am quickly running out of things to try on this...

I installed Mythbuntu 10.10 and.... exact same thing!  I was hoping it would fix it.  Total clean install.

---

