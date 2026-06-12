---
title: "Zotac HD-ID11 - HDMI No DIGITAL Audio"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Jynks on 2011-01-02
Hi there....

I still can not get HDMI audio workign on my zotac.. there is a lot of post that talk about it here but i can not seam to get any of them to work, and may are pre mavrick...

I made a sim post a while back about ubuntu but no one replied.... 


I am no truing xubuntu but still no luck

Dose anyone have any idea what I am meant to do here?

Like there is this post but it is from 2009... so all the inputs are wrong...
[http://ubuntuforums.org/showpost.php?p=7328686&postcount=52](http://ubuntuforums.org/showpost.php?p=7328686&postcount=52)

<--- Edit

Here is some more info that might help

I am using a fresh install of xubuntu off the official desktop ISO from the xubuntu site. All i have done is install, activate the NVIDIA hardware drivers, reboot, then download and apply the 150 or so updates though the update manager.

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2011-01-02
See this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

