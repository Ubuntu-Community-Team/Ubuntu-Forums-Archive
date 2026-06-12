---
title: "Sound Choppy &amp; Distored"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Otto-C on 2010-11-04
Using Ubuntu 10.04 32 bit.  Original install from an Ubuntu disk from Canonical.
All updates completed.
When trying to use Skype the sound is badly distorted on both ends.
When playing music or video the sound is just fine.

Any help or ideas most welcome.
tia
otto-c

Below is some of my system information.

otto@desktop:~$ uname -a
Linux otto@desktop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010

otto@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

otto@desktop:~$ lspci
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

otto@desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                              0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  libsnack2-alsa                            2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
ii  xmms2-plugin-alsa                         0.7DrNo-4ubuntu1                                XMMS2 - ALSA output

otto@desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                              0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  libsnack2-alsa                            2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
ii  xmms2-plugin-alsa                         0.7DrNo-4ubuntu1                                XMMS2 - ALSA output

otto@desktop:~$

tia
otto-c

---

