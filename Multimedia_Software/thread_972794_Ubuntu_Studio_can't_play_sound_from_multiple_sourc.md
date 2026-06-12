---
title: "Ubuntu Studio can't play sound from multiple sources concurrently"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Chua-Chua on 2008-11-06
Hello,

I am using Ubuntu Studio 8.04 and I whenever I have more than one application using the sound driver, another application can't play sound.

For example, I am viewing youtube videos and I open Rhythmbox. Rhythmbox can't play any sound because the Flash locked the sound driver. What I have to do is close Firefox before I can use another application which plays sounds. When I close the app, I hear a click or snap.

$uname -r 
2.6.24-21-rt

I think Ubuntu Studio is using ALSA right now.

Thanks

---

### Post by Chua-Chua on 2008-11-06
aplay -l brings up this

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

