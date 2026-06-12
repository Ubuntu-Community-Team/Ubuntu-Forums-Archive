---
title: "No sound in Xubuntu 9.04 - Toughbook CF-19"
date: 2009-09-04
forum: Multimedia Software
---

### Post by nightmicu on 2009-09-04
Hi everyone,

   I am running Xubuntu 9.04 off a USB drive on a Panasonic Toughbook CF-19. So far everything has gone fairly well but I cannot get any sound.

I followed a [tutorial]("https://help.ubuntu.com/community/OpenSound") to switch to OpenSound, everything would appear to have installed correctly but still no sound. When I open the OSSXMIX panel, however, the volume bars are moving and nothing appears to be muted. Also, the Function keys for audio on the keyboard do not respond.

Does anyone have any ideas?

Thanks, 

Ben

---

### Post by xraynetcontrol on 2013-03-21
I know this is an old thread, but here is what I did to get it working on my CF-29:

In terminal, open this:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
In the file that opens up, down at the bottom, add this:
```
options snd-hda-intel model=generic
```
If that doesn't work after a reboot, change "generic" to "INTEL"

---

### Post by howefield on 2013-03-21
Old thread closed.

---

