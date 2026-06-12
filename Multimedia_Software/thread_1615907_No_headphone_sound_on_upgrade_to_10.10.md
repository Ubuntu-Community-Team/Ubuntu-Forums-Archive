---
title: "No headphone sound on upgrade to 10.10"
date: 2010-11-07
forum: Multimedia Software
---

### Post by pafindr on 2010-11-07
Hey gang I upgraded from 10.04 to 10.10 and lost headphone sound. My external speakers are working fine though.
I've tried Pulse Audio and Alsa Mixer to no avail. :(
Any help will be appreciated.

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by pafindr on 2010-11-07
I should have listed my specs :rolleyes:

Running a desktop with Asus M4A78T-E AMD
Dual boot to WinXP
The headphones work when I boot to WinXP

```
Linux hector-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
hector@hector-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
hector@hector-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                            1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                            4.69-0ubuntu2                                     Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                         ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.30-2                                         GStreamer plugin for ALSA
ii  libsnack2-alsa                        2.2.10-dfsg1-9                                    Sound extension to Tcl/Tk and Python/Tkinter - Tcl/Tk library
hector@hector-desktop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

==> /proc/asound/card2/codec#0 <==
Codec: ATI RS690/780 HDMI

```

---

### Post by pafindr on 2010-11-08
Anyone?

---

### Post by pafindr on 2010-11-09
SOLVED showed up that it was a bios setting that was wrong. Front panel audio was set to HD where it should be AC97

---

