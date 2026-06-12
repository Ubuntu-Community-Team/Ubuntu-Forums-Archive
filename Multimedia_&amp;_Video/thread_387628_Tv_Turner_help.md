---
title: "Tv Turner help"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by Icemanyurt on 2007-03-18
On my system I have a MSI TV Anywhere Plus turner card, but I can't figure out how to use TvTime

I am pretty sure I have the correct drivers installed, any would be great

Output of lspci
> 02:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

Relevant portion of dmesg (I think)
> 
[17179587.532000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[17179587.532000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 209
[17179587.532000] saa7133[0]: found at 0000:02:0a.0, rev: 208, irq: 209, latency: 64, mmio: 0xff5df800
[17179587.532000] saa7133[0]: subsystem: 1462:8624, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179587.532000] saa7133[0]: board init: gpio is 40


[17179587.676000] saa7133[0]: i2c eeprom 00: 62 14 24 86 10 28 ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.676000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.680000] saa7133[0]: registered device video0 [v4l2]
[17179587.680000] saa7133[0]: registered device vbi0
[17179587.716000] saa7134 ALSA driver for DMA sound loaded
[17179587.716000] saa7133[0]/alsa: saa7133[0] at 0xff5df800 irq 209 registered as card -1


---

### Post by crispy_420 on 2007-03-18
Try launching tvtime via command line. If there error here we can narrow down the cause of your issues.

Or maybe the drivers just aren't loading by default. You may have to add that into /etc/modules.

---

### Post by Icemanyurt on 2007-03-18
I had no errors on launching from command line.

etc/modules is pretty much empty, and I am not sure what to add

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


---

### Post by crispy_420 on 2007-03-18
My next guess is that you have to tell the Ubuntu to load the TV tuner module on boot. I don't have the same card as you (mine is a bt878).

Here are some links that may lead you in the right direction:

[http://linuxtv.org/v4lwiki/index.php/Saa7134-alsa](http://linuxtv.org/v4lwiki/index.php/Saa7134-alsa)

[http://gentoo-wiki.com/HARDWARE_saa7134#Setup_Modules](http://gentoo-wiki.com/HARDWARE_saa7134#Setup_Modules)

[http://www.ubuntuforums.org/showthread.php?p=378283](http://www.ubuntuforums.org/showthread.php?p=378283)

---

### Post by Icemanyurt on 2007-03-18
Thanks!
I will give that a try

---

