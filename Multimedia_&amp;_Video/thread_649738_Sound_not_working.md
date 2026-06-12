---
title: "Sound not working"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by fourthofjuly on 2007-12-25
Sound works in Windows XP, but not in Ubuntu 7.04, Fedora 7 and OpenSuSE 10.1. No sound at all.

   1. I have an Intel D845GCL original motherboard with on-board sound, Pentium D 3.0 GHz, 160 GB SATA HDD & 1GB RAM.
   2. In Ubuntu sound preferences, under Default Mixer Tracks, listed device are HDA Intel (ALSA mixer) and SigmaTel STAC9221 A1 (OSS Mixer).
   3. I have tried disabling sound from BIOS, applied the latest updates of Fiesty, but nothing seems to work.

Could anyone be kind enough to guide me in making sound work on my system?

I have following details from lspci command:

devang@desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

Thanks & With Warm Regards,

Devang.

---

### Post by Casual Fan on 2007-12-25
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

this might help...good luck :)

---

### Post by fourthofjuly on 2007-12-26
thank you so much, looks tricky, but I shall certainly try it out...

---

