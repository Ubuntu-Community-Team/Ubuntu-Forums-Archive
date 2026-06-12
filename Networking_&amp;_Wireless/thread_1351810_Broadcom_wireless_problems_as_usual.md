---
title: "Broadcom wireless problems as usual"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by madm0nk on 2009-12-10
lspci -v output:

05:02.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
	Subsystem: Netgear Device 7d00
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
	Kernel driver in use: wl
	Kernel modules: wl, ssb


The only way I can get this working AT ALL is to activate the Broadcom STA Wireless Driver when booted with the livecd BEFORE installing the OS. Then in order to get it to work slightly better after installation I have to follow the instructions here [http://ubuntuforums.org/archive/index.php/t-1341538.html](http://ubuntuforums.org/archive/index.php/t-1341538.html) (just unzip run make then modprobe lib80211; insmod wl.ko). BUT ... after this "works" my wireless fails at random times. It looks like the module is failing since after my wireless DC's I can't see any networks with wicd and iwconfig shows no wireless interface. If I run "sudo rmmod wl" and then "modprobe lib80211; insmod wl" then BAM! everything is back in order and I can reconnect only to fail a short time later ... rinse and repeat. Problems with wireless technology is hurting linux like the plague. I understand that the hardware vendors are mostly at fault here but still. This needs to be TOP PRIORITY!!! We don't need a fancy new login screen, we don't need flashy new desktop features we need to get the whole wireless internet problem worked out FIRST!! /rant

Note: This is with 9.10

---

### Post by madm0nk on 2009-12-13
Nobody else is having this problem? Really?

---

