---
title: "Jittery/Stuttering Sound Problems"
date: 2009-03-09
forum: Multimedia Software
---

### Post by waltons_pacman on 2009-03-09
Howdy:
recently did a fresh install on a friends comp, a laptop hp pavillion dv4 and works like a charm. Save for the sound which 'skips' or 'jumps' or 'jitters' or 'stutters'.
however you wanna put it.

on a fresh boot, the alsamixer has nothing in it. no controls at all.
after
```
sudo alsa force-reload
```
the alsamixer has the correct number of controls.
the output from aplay -l:
```
***** list of PLAYBACK hardware Devices ******
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
    Subdevices: 1/1
    Subdevices #0: subdevice #0
```

output from lspci:
```
00:lb.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

{-================================================================
 - if anyone has this problem, or knows of someone who does, or has a solution, please post!
 -}

---

