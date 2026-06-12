---
title: "No sound on Gateway MX3215 w/ Ubuntu 9.0.4"
date: 2009-10-25
forum: Multimedia Software
---

### Post by MontoyaF1 on 2009-10-25
Hi, I'm still noob to Ubuntu and am not a computer whiz.  I installed Ubuntu 9.0.4.  My Gateway uses an onboard sound card with the Via 8237 chipset.  I have done the following:

1.  Checked that volume control was toggled to VIA 8237 (Alsa Mixer)
2.  Nothing is muted and volume is up all the way
3.  Checked to see if the soundcard was disabled in the system's BIOS, but I didn't see the soundcard anywhere in the BIOS
4. Started following these directions:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

5.  Executed aplay -l at it shows that something is there:

> **** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #06.  Typed  lspci -v and it appeared to list my soundcard
7.  Typed modinfo soundcore and got

> filename:       /lib/modules/2.6.28-15-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     73D4C7B18BCDAF17EE3F9B5
depends:       
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 8.  Typed sudo modprobe snd-via82xx and didn't get an error, neither did any sound occur
9.  Went to sudo nano /etc/modules and added the last line so that it looks like this:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-via82xx10.  Rebooted and still no sound
11.  I went to the Alsa site and cannot find the module that I'm supposed to download.  I am guessing it is alsa-driver-1.0.9rc4a.tar.bz2 and I put it in a new directory I created called /usr/src/alsa

Now what?  Did I screw something up earlier in the steps?

---

### Post by MontoyaF1 on 2009-10-27
Anybody? :(

---

### Post by Ulysses361 on 2009-10-28
Please try this solution:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=507505](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=507505)

---

### Post by MontoyaF1 on 2009-10-30
Thanks, that worked!  That was the easiest thing I've ever had to do in Ubuntu.  :D

---

