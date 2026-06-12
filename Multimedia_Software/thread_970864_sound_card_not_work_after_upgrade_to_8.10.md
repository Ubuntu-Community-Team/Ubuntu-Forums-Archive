---
title: "sound card not work after upgrade to 8.10"
date: 2008-11-04
forum: Multimedia Software
---

### Post by caomo on 2008-11-04
I'm using Asus M2N laptop.
In 8.04, sound card work after I add "acpi_irq_isa=7 noapic" to my boot option.
But after upgraded to 8.10, it don't work anymore. Any idea? Thanks!
Following are some information.
~$ lspci |grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

~$ cat /dev/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux caomo-laptop 2.6.27-7-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG

---

### Post by caomo on 2008-11-04
More details:
~$ lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1713
	Flags: medium devsel
	I/O ports at e000 [size=256]
	I/O ports at e100 [size=64]
	Memory at 30000400 (32-bit, non-prefetchable) [size=512]
	Memory at 30000600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0
~$ aplay -l
aplay: device_list:215: no soundcards found...

~$ cat /proc/asound/cards 
--- no soundcards ---
 ~$ modprobe snd-intel8x0
NO error message provided, seems succeed. but still have no sounds, and found no soundcards by previous commands.
Anyone could help? 
Thanks a lot!

---

### Post by caomo on 2008-11-07
I solved it by myself by reinstall all sound drivers by following [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) packages 'gdm' and 'ubuntu-desktop' and 'gdm-guesssession' are removed after removing the linux-sound-base packages. do the following
Code:

sudo apt-get install gdm ubuntu-desktop gdm-guesssession

---

