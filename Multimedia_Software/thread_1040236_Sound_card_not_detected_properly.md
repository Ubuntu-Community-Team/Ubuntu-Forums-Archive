---
title: "Sound card not detected properly?"
date: 2009-01-15
forum: Multimedia Software
---

### Post by Black_Monkey on 2009-01-15
Hi, I'm getting no sound at all in 8.10.
In the Multimedia section of System Settings, I have the options:
PulseAudio
HDA Intel (STAC92xx Analog)
[COLOR="Gray"]HDA Intel (STAC92xx Digital)
HDA Intel, STAC92xx Digital (IEC958 (S/PDIF) Digital Audio Output)[/COLOR]

The second 2 options are greyed out, and when booting X it told me that they could not detect them, and asked me whether I wanted to forget them.
aplay -l gives:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Although it said 0/1 subdevices before, I've done a sudo modprobe snd-hda-intel since then if that makes a difference.

I think the sound suddenly went somewhere around that time that I installed KDE 4.2 beta 2 or when I changed my graphics driver a couple of times.

---

### Post by Black_Monkey on 2009-01-24
Sorry to bump, but can anyone help? I've had no sound for ages now.

---

