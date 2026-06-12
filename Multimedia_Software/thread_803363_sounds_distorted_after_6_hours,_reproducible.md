---
title: "sounds distorted after 6 hours, reproducible"
date: 2008-05-22
forum: Multimedia Software
---

### Post by hekkel on 2008-05-22
Anyone else seen this? Since installing Hardy my sound becomes distorted after an uptime of about 6 hours. Very reproducible.

lspci says I have:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

This is on a Dell optiplex 745.

---

### Post by Zorael on 2008-05-22
Since it's an Intel HDA card there's a chance that [this](http://ubuntuforums.org/showthread.php?p=5017453#post5017453) might be relevant. Your issue seems quite different from the one I experienced, though. It could be hardware failure for all I know.

---

### Post by wandalalakers on 2008-07-12
I experience this problem with the flash player.  I have to reboot my pc in order for flash videos to not sound distorted.

HDA sound card using Realtek ALC662 chipset.

Asus motherboard
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

