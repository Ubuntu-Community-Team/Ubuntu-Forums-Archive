---
title: "can't load dvb drivers after upgrade"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by deepkamal on 2007-11-03
Hi,
I originally installed Feisty 7.04.  My twinhan dvb-s card worked just fine (/dev/dvb has been on boot).  
Recently, I let the Update Manager upgrade my system to 7.10 and the twinhan dvb-s card stopped working (no /dev/dvb is created on boot).  I get the following stuff in dmesg:
[   41.590797] bttv: driver version 0.9.17 loaded
[   41.590806] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   41.590916] bttv: Bt8xx card found (0).
[   41.590957] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (lev
el, low) -> IRQ 11
[   41.590973] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 11, latency: 32, mmio
: 0xdddfe000
[   41.590986] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   41.591015] bttv0: gpio: en=00000000, out=00000000 in=00feffff [init]
[   41.591124] bttv0: using tuner=4
[   41.616679] bttv0: add subdevice "dvb0"
[   41.654116] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.687150] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.691303] bt878: AUDIO driver version 0.0.0 loaded
[   41.691367] bt878: Bt878 AUDIO function found (0).
[   41.691399] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [LNKB] -> GSI 11 (lev
el, low) -> IRQ 11
[   41.691409] bt878_probe: card id=[0x0], Unknown card.
[   41.691411] Exiting..
[   41.691417] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[   41.691423] bt878: probe of 0000:00:09.1 failed with error -22
[   41.837659] dvb_bt8xx: unable to determine DMA core of card 0,
[   41.837666] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try
 removing it.
[   41.837673] dvb-bt8xx: probe of dvb0 failed with error -14

When I pick the second kernel choice in grub to boot, the dvb-s card works again.
The grub choices are:
 Ubuntu 7.10, kernel 2.6.22-14-generic
 Ubuntu 7.10, kernel 2.6.20-16-generic

booting into the 2.6.20-16 kernel makes the dvb-s card work but the Xserver doesn't start with good video resolution because the wrong video drivers are loaded (??)

I would like to get the 2.6.22-14 kernel going with the dvb-s card.  What, if anything, can I do?

thanks...

---

### Post by jedix on 2007-12-09
i have the same problem.  I have two tuners and for some reason, the driver tries to use dvb0 (which doesn't seem to be the right one..)

---

### Post by barmax on 2007-12-30
> **deepkamal said:**
> Hi,
I originally installed Feisty 7.04.  My twinhan dvb-s card worked just fine (/dev/dvb has been on boot).  
Recently, I let the Update Manager upgrade my system to 7.10 and the twinhan dvb-s card stopped working (no /dev/dvb is created on boot).  I get the following stuff in dmesg:
[   41.590797] bttv: driver version 0.9.17 loaded
[   41.590806] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   41.590916] bttv: Bt8xx card found (0).
[   41.590957] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (lev
el, low) -> IRQ 11
[   41.590973] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 11, latency: 32, mmio
: 0xdddfe000
[   41.590986] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   41.591015] bttv0: gpio: en=00000000, out=00000000 in=00feffff [init]
[   41.591124] bttv0: using tuner=4
[   41.616679] bttv0: add subdevice "dvb0"
[   41.654116] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.687150] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.691303] bt878: AUDIO driver version 0.0.0 loaded
[   41.691367] bt878: Bt878 AUDIO function found (0).
[   41.691399] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [LNKB] -> GSI 11 (lev
el, low) -> IRQ 11
[   41.691409] bt878_probe: card id=[0x0], Unknown card.
[   41.691411] Exiting..
[   41.691417] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[   41.691423] bt878: probe of 0000:00:09.1 failed with error -22
[   41.837659] dvb_bt8xx: unable to determine DMA core of card 0,
[   41.837666] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try
 removing it.
[   41.837673] dvb-bt8xx: probe of dvb0 failed with error -14

When I pick the second kernel choice in grub to boot, the dvb-s card works again.
The grub choices are:
 Ubuntu 7.10, kernel 2.6.22-14-generic
 Ubuntu 7.10, kernel 2.6.20-16-generic

booting into the 2.6.20-16 kernel makes the dvb-s card work but the Xserver doesn't start with good video resolution because the wrong video drivers are loaded (??)

I would like to get the 2.6.22-14 kernel going with the dvb-s card.  What, if anything, can I do?

thanks...

Hi,

Have you solved your problem yet and if so what was the slution?

Regards

---

### Post by mieze on 2008-01-12
Hi,

I had a similar problem and could solve it. Please read this posting

[http://www.suseforums.net/index.php?showtopic=41573&pid=222748&mode=threaded&show=&st=&#entry222748](http://www.suseforums.net/index.php?showtopic=41573&pid=222748&mode=threaded&show=&st=&#entry222748)

---

