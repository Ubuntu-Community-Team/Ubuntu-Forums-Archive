---
title: "No surround sound on ga-m61pme-s2 ALC662"
date: 2009-04-08
forum: Multimedia Software
---

### Post by covert on 2009-04-08
I have a Gigabyte ga-m61pme-s2 with ALC662 audio. 2 channel audio works just fine. I have just purchased from 5.1 speakers and I am unable to get any output besides Front left and Front right.

aplay -L

```
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

No /etc/asound.conf file found
No ~/.asoundrc file found

aply -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

when I run "speaker-test -Dplug:surround51 -c6 -l1 -twav" only Front left and Front right make any sound.

alsaconfig version 1.0.18rc3

2.6.27-4-generic #1 SMP Wed Sep 24 01:29:06 UTC 2008 x86_64 GNU/Linux


How can I get 5.1 sound working ?

---

### Post by covert on 2009-04-09
Solved it. Upgraded to alsa 1.0.19 with help form this thread
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

go build errors at first and had to edit alsa-driver-1.0.19/drivers/pcsp/pcsp.patch and alsa-driver-1.0.19/acore/hrtimer.patch files to stop the build error. Part to edit will be obvious if you get the same build errors in hrtimer.c and then pcsp.c

After a good install and reboot run alsamixer and scroll all the way right and change chans from 2 to 6

[edit]I would set this as solved if I could work out how to set it.

---

