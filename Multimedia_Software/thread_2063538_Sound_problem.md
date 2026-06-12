---
title: "Sound problem"
date: 2012-09-27
forum: Multimedia Software
---

### Post by gosling1 on 2012-09-27
By mistake, I pressed one of the volume buttons on my K260 Logitach wireless keyboard. Now there is no audio at all.

Looks like the sound card is recognized.

michael@michael-ET1352:~$ sudo aplay -l
[sudo] password for michael: 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
michael@michael-ET1352:~$ 

What else should I be looking for?

Many thanks in advance.

Cheers,

MikeR

---

### Post by Ares Drake on 2012-09-27
check via alsamixer in the terminal that it is not muted. (press m to unute).

---

