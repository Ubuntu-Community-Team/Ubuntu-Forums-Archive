---
title: "Upgraded from 9.10 to 10.04 now sound only works sometimes"
date: 2010-07-08
forum: Multimedia Software
---

### Post by ardnut on 2010-07-08
Since upgrading from 9.10 to 10.04 sound now only works some of the time.  One boot it will work perfectly and another boot it wont, the gnome sound mixer basically says that it can't detect a sound card.

I've compared lsmod when it does vs doesn't work and I've noticed...

Working:
```
Module                  Size  Used by
snd_hda_intel          21877  1 
```

Not working:
```
Module                  Size  Used by
snd_hda_intel          21877  0
```

So it seems like the driver/module isn't detecting or initialising my card on some boots.

Any ideas how to fix this or how to debug any further?

Thanks,
Ash

---

### Post by ardnut on 2010-07-08
I have the following on board sound card...

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

---

### Post by lidex on 2010-07-09
Try this first.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

No help? Can you post the output of these terminal commands for me please:
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

### Post by ardnut on 2010-07-13
Sorry for delay in reply the nature of the bug means that it only only occurs sometimes.  I haven't yet been able to reproduce it on the original machine but same problem on another which also uses the intel driver/module.

Looks like these files/folders didn't exist to begin with, so it didn't resolve the issue...
```
$ rm -r ~/.pulse ~/.asound* 
rm: cannot remove `/home/ardnut/.asound*': No such file or directory

$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory
```

Here's the output of the other commands...

```
$ uname -a
Linux mythtv 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

$ aplay -l
aplay: device_list:223: no soundcards found...

$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                         0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  libsdl1.2debian-alsa                 1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                      14.3.0-1.1build1                                SoX alsa format I/O library

$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1986A
```

---

### Post by ardnut on 2010-07-13
On a boot when sound is working I get this in comparison...

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-07-13
We may be able to figure this out. What is the make/model of pc in question? How many audio jacks?

---

### Post by Yellow Pasque on 2010-07-13
On a boot with no sound, look through dmesg to see why the kernel module isn't loading.
```
dmesg | more
```

---

### Post by ardnut on 2010-07-15
Self built PC using the following motherboard with on board sound (single stereo output jack)...

ASUS M2NPV-VM


I've captured the output from dmesg for a sound vs no sound boot and I can't see any differences in terms of intel, hda, alsa, nvidia, snd, etc... or any error messages about sound or modules not loading/failing.

---

