---
title: "I can't get my microphone to work."
date: 2011-04-02
forum: Multimedia Software
---

### Post by gladbagz on 2011-04-02
My integrated microphone will not work and I think I have tried every  suggestion on other threads.  My laptop is a Compaq  Presario V6000.  Here is the rest of my info.

# uname -a
Linux laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 26 2011 for kernel 2.6.35-28-generic (SMP).

# head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20549 (Venice)

My Alsa information is at [http://www.alsa-project.org/db/?f=c99997f12271e22b1ec370d4d360c26359f6f4dd](http://www.alsa-project.org/db/?f=c99997f12271e22b1ec370d4d360c26359f6f4dd)

Help would be appreciated.  I just want to talk to my wife and children over skype while I am gone.

---

### Post by lidex on 2011-04-03
What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by gladbagz on 2011-04-03
Thank you for helping me.  Here is what you asked for.

# dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.23+dfsg-1ubuntu4                       ALSA driver configuration files
ii  alsa-utils                                     1.0.23-2ubuntu3.4                          Utilities for configuring and using ALSA
ii  bluez-alsa                                     4.69-0ubuntu2                              Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.30-2                                  GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                           1.2.14-6ubuntu3                            Simple DirectMedia Layer (with X11 and ALSA options)
ii  linux-alsa-driver-modules-2.6.35-28-generic    2.6.35-28.201104011600                     Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots

---

### Post by lidex on 2011-04-03
Looks like alsa is selecting 'laptop-hpsense' as your model based on your 'auto' entry in alsa-base.conf. Probably need to force a different model as that one is not correct. Remove it, reload alsa, and run the info script again please.

```
sudo alsa force-reload
```

---

### Post by gladbagz on 2011-04-04
Thanks for the help lidex.  I was able to get my mic working.  I got a little impatient and decided to try installing Kubuntu 10.10 to see if I could get my mic to work on it.  After a lot of trial and error, I am able to use an external microphone by muting the external microphone in the various sound settings and treating it as an internal microphone instead.  Not sure why or how this works but it does.  One of these days I may go back to Ubuntu and see if I can replicate my results.

FYI.  Starting with 10.10, Kubuntu now uses Pulseaudio.  I figured out my mic issue while I had Pulseaudio uninstalled and my voice was coming through low with lots of static.  Once I re-installed Pulseaudio though, my voice came through loud and clear.

---

