---
title: "Sound Problems"
date: 2010-07-08
forum: Multimedia Software
---

### Post by cones on 2010-07-08
I'm having sound problems.  I get sound but it sounds horrible. It seems to be worse when i'm playing something in xbmc. When i type this command ```
aplay -l
``` i get this ```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```  I'm not sure what i can do to get this working.

---

### Post by lidex on 2010-07-09
What version of ubuntu and was it a fresh install or upgrade?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by cones on 2010-07-09
Actualy its working now.  I just got a graphics card and the problem has stopped.  I have no clue how that would afect the sound.  If you want i can post the output of those codes.

---

