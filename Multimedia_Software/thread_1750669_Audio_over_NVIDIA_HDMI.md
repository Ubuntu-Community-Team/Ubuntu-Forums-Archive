---
title: "Audio over NVIDIA HDMI"
date: 2011-05-05
forum: Multimedia Software
---

### Post by EagleG33k on 2011-05-05
I've been struggling with this on and off for the past few months and have yet to find a decent solution.  I cannot get good quality audio over HDMI.  Most of the threads I've read on this are from 2008 or so, and I'm hoping that someone will be able to give me updated information.  Currently I'm getting no audio at all over HDMI, though recently I was getting some rather poor audio working.  However, after updating to the latest NVIDIA driver, I've lost even that.  Video however, works fine.

Here's some details on my setup:
Advanced Linux Sound Architecture Driver Version 1.0.23.
Proprietary NVIDIA driver 270.41.06 (previously had 260.19.06 and bad quality audio)
NVIDIA GT 330M card
kernel 2.6.35-28-generic
Running 64bit Ubuntu 10.10

Also - in alsamixer S/PDIF is not muted and in sound preferences HDMI out is selected.

Any help is greatly appreciated!

---

### Post by lidex on 2011-05-05
See this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by EagleG33k on 2011-05-06
Well, I'm now up to ALSA version 1.0.24, but still no audio.  I gave the suggestions a shot, but most of them are working for people running different NVIDIA cards and/or 32bit ubuntu.

After reading some of the suggestions here's more info on my setup:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card1/eld#* | grep eld_valid
eld_valid        0
eld_valid        0
eld_valid        0
eld_valid        0

Anything else for me to try?

---

### Post by lidex on 2011-05-06
What is this output:
```
grep eld_valid /proc/asound/NVidia/eld*
```

---

### Post by EagleG33k on 2011-05-06
```

$ grep eld_valid /proc/asound/NVidia/eld#*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0

```

---

### Post by BicyclerBoy on 2011-05-07
You have to have the AVR HT Amp & possibly the TV turned on when you run that command..

You may need to power up all the HDMI gear in controlled sequence to make sure ..
I not joking..some MythTV users have to do this to get HDMI sh#t to work..

---

