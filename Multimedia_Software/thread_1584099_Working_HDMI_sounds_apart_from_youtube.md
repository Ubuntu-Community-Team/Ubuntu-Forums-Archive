---
title: "Working HDMI sounds apart from youtube"
date: 2010-09-28
forum: Multimedia Software
---

### Post by booah on 2010-09-28
Hey,

I can get sound over HDMI for videos, mp3s, OS sounds etc but I can't get anything over youtube, google videos etc. I have the latest alsa installed, my aplay -l is
```
shuttle@shuttle-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

in sys->pref->sounds under **hardware** i only have :
High definition audio controller
1 output
analog stereo output

**Output** :
High definition audio controller Analog Stereo

There is no mention of HDMI output there which is surprising to me but aside from youtube HDMI is working perfect. Any help is very much appreciated, cheers

---

### Post by booah on 2010-09-28
ok I got the sound working on youtube by creating an .asoundrc file in my home directory with the following
```
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:17"
}
}
```credit goes to this guide:
[http://blog.mybarachois.com/b1/play/xbmc/htpc-nvidia-ion-1080pxbmcubuntu-guide/](http://blog.mybarachois.com/b1/play/xbmc/htpc-nvidia-ion-1080pxbmcubuntu-guide/)

edit: forgot to mention that I cannot play an mp3/movie while i am streaming a youtube video. Seems my way isn't the best for multitasking. Well cant have it all i guess :)

---

