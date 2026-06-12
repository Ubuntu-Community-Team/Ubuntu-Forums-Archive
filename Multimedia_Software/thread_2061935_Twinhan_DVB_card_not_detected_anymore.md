---
title: "Twinhan DVB card not detected anymore"
date: 2012-09-23
forum: Multimedia Software
---

### Post by schneil on 2012-09-23
Hi all

I'm running ubuntu 12.04 64bit.  I have an old PCI DVB-T card that I use to watch freeview TV.  It ran fine in ubuntu until today.  Me-TV keeps saying "there are no dvb devices available"

Can anyone help??


neil@quadcorefatty:~$ dmesg | grep bt
[    0.412806] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.412822] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.412824] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.412826] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.412829] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.412831] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xffffffff] (subtractive decode)
[   23.716998] bttv: driver version 0.9.19 loaded
[   23.717001] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   23.717049] bttv: Bt8xx card found (0)
[   23.717062] bttv 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   23.717073] bttv: 0: Bt878 (rev 17) at 0000:05:02.0, irq: 18, latency: 64, mmio: 0xfdffe000
[   23.717265] bttv: 0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   23.723671] usbcore: registered new interface driver btusb
[   23.748978] bttv: 0: tuner type unset
[   23.750225] bttv: 0: registered device video1
[   23.750281] bttv: 0: registered device vbi0

There's a device in /dev/video for it, but looking at dmesg it's not loading up the dvb modules anymore.  Why is this?  It's a Brooktree 878 chipset. Used to work 100% in ubuntu out of the box.

Manually modprobing the drivers according to [http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Digital_Terrestrial_TV_Card_Ter](http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Digital_Terrestrial_TV_Card_Ter)
doesn't create /dev/dvb either.

Help!



lspci -vn

05:02.0 0400: 109e:036e (rev 11)
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fdffe000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: bttv
	Kernel modules: bttv

---

### Post by schneil on 2012-09-25
I think the card is dead, tried it on my old windows xp box and had no luck with drivers.  So going to get another card

---

