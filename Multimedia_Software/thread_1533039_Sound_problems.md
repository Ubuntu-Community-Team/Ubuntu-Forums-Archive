---
title: "Sound problems"
date: 2010-07-17
forum: Multimedia Software
---

### Post by joek71 on 2010-07-17
Hi guys

I have the latest ubuntu and i am using motherboard DFI Expert, and i get sound distortion, can someone please help me out with this.

thanks

---

### Post by lidex on 2010-07-18
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

Also in a terminal enter:
```
alsamixer
```
Check your levels are not too high.

---

### Post by joek71 on 2010-07-18
uname -a
Linux joe 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux


aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
joe@joe:~$ ^C
joe@joe:~$ ^C
joe@joe:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                                   ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                          ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                            Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                                GStreamer plugin for ALSA
ii  libesd-alsa0                         0.2.41-6ubuntu1                                          Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                 1.2.13-4ubuntu4                                          Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                      14.3.0-1.1build1                                         SoX alsa format I/O library

head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

---

### Post by lidex on 2010-07-18
Can you describe the distortion? Is it constant or sporadic? A crackling sound, buzzing, etc? Can you post a screen shot of alsamixer? Try changing your profile in sound preferences on the hardware tab.

---

