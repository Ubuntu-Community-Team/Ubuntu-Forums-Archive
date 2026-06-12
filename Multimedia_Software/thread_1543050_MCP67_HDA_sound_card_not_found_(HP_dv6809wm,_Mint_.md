---
title: "MCP67 HDA sound card not found (HP dv6809wm, Mint 9)"
date: 2010-07-31
forum: Multimedia Software
---

### Post by mumpspro on 2010-07-31
I have tried many, many things to try to get the sound card recognized since upgrading from Mint 8 to Mint 9, and have still been unsuccessful...all modules and up to date and alsa was rebuilt this morning (to insure I didn't mess something up with my prior attempts to resolve).  I have only been using Linux for about a month now, and really don't want to have to go back to Windows :(

Here is a link to my latest hardware and troubleshooting info:

[http://forums.linuxmint.com/viewtopic.php?f=90&t=52531&p=302076#p302076]("http://forums.linuxmint.com/viewtopic.php?f=90&t=52531&p=302076#p302076")

Can someone on this forum please assist?

---

### Post by lidex on 2010-08-01
Can we pare that down a tad? Remove the custom entries from alsa-base.conf and reboot. Now these command outputs please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Was this an upgrade or fresh install? If upgrade did you remove any old sound config tweaks? What had you done on the previous install for audio?

---

### Post by mumpspro on 2010-08-06
The make/model of the laptop was in the subject, but here it is again if you missed it:  

HP Pavillion dv6809wm

Not sure what fixed it, but **when I booted this morning I had sound**...the recent changes to the system included installation of a few Second Life flavors (Imprudence and Emerald) and whatever updates came through yesterday on Mint Update.  I had no sound last night prior to reboot, so I think I can narrow it down to those.

[I]If someone can tell me how, I'll post all recent updates...maybe that will help others fix this issue if they have the same...
[/I]


Here are the previously requested outputs (although not sure if they will help find the original issue to assist others):

```
mumpspro@mumpspro-laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mumpspro@mumpspro-laptop ~ $ uname -a
Linux mumpspro-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
mumpspro@mumpspro-laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mumpspro@mumpspro-laptop ~ $ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-modules-2.6.32-23-generic                 1.0.22.1+dfsg-0ubuntu3+2.6.32-23.37             ALSA modules for kernel 2.6.32-23-generic
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                     1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                   0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  linux-alsa-driver-modules-2.6.32-22-generic    2.6.32-22.201007050500                          Ubuntu-supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-23-generic 2.6.32-23.16                                    Ubuntu supplied Linux modules for version 2.
ii  linux-headers-alsa-driver-2.6.32-22-generic    2.6.32-22.201007050500                          Header files related to linux-alsa-driver-mo
mumpspro@mumpspro-laptop ~ $ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20561 (Hermosa)

```

---

