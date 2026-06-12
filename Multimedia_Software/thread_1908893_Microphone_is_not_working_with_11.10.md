---
title: "Microphone is not working with 11.10"
date: 2012-01-14
forum: Multimedia Software
---

### Post by aleoo on 2012-01-14
Hi,

I'm trying to solve this problem with the latest version of ubuntu (11.10).
I had the same issue before upgrading, and I got through it;
but this time I don't know what to do. 
I have an Acer Aspire 3680, Skype version is 2.2.0.35 .
If anyone can help me and tell me what information or commands in terminal are needed for troubleshooting, I will be glad to post all the outputs you request.
Thanks in advance

Alex

---

### Post by aleoo on 2012-01-14
Sorry for the thread title, the word "Skype" is missing.

Here are some outputs from the terminal:

```
pc:~$ uname -a
Linux pc 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pc:~$ dpkg -l | grep "alsa"
ii  alsa-base                              1.0.24+dfsg-0ubuntu2                       ALSA driver configuration files
ii  alsa-utils                             1.0.24.2-0ubuntu8.1                        Utilities for configuring and using ALSA
ii  bluez-alsa                             4.96-0ubuntu4                              Bluetooth ALSA support
ii  gnome-alsamixer                        0.9.7~cvs.20060916.ds.1-2.1ubuntu0.1       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                     0.10.35-1                                  GStreamer plugin for ALSA

pc:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054
```

---

### Post by aleoo on 2012-01-15
My internal mic does not work with sound recorder neither, 
even if I care more about let other skype users listen to my voice.
I forgot to say that I also have Pulse Audio installed.

---

### Post by aleoo on 2012-01-15
I apologize for bothering or annoying: I solved choosing the front-mic in the sound settings.

---

