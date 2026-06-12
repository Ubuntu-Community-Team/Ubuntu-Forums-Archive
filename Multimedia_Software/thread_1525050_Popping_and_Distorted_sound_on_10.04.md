---
title: "Popping and Distorted sound on 10.04"
date: 2010-07-06
forum: Multimedia Software
---

### Post by Ericj1186 on 2010-07-06
So, I did a clean install to 10.04.   Not too many issues except any sound I play sounds like it's underwater and pops while playing.  I have tried to do the Pulse Audio install, but every time I loaded pauvcontrol (I think was the title), it would pop up "Connection Failure: Connection Refused."   I tried to follow other guides, but they'd all fail because I'd be missing half of the files it changed.

I have a Creative Labs X-Fi Fatality card that has given me troubles in the past, but usually, it works.  I tried to install Creative's open driver, but again, I had an error when I attempted to Make the directory.

Any suggestions?  I can post outputs if my post was too ambiguous.  Thanks for any help.

---

### Post by lidex on 2010-07-06
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

### Post by Ericj1186 on 2010-07-06
I had surgery today, so I'm a bit off, but I'll post the results tomorrow.

The computer is a custom build.

Thanks

---

### Post by Ericj1186 on 2010-07-08
Sorry for the delay:
**uname -a**
```
Linux eric-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**dpkg -l | grep "alsa"**
```
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA

```


**head -n 1 /proc/asound/card*/codec#***
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

Guessing I did the last one wrong...

---

### Post by lidex on 2010-07-08
No, those codecs won't show up there. Are you using the X-fi or onboard sound?

---

### Post by Ericj1186 on 2010-07-08
It reverts to onboard, but my speakers are through X-Fi.  When I set it as X-Fi, that is where the popping speakers come from.  I have no sound, obviously, if I set it as onboard.

---

### Post by lidex on 2010-07-10
Try disabling the onboard audio in bios.

---

