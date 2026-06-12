---
title: "Very poor sound quality."
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by sluzi26 on 2007-01-01
Hi there, I own a Toshiba P105-S9722 with the following LSPCI Output

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0298 (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
0a:04.2 Mass storage controller: Texas Instruments Unknown device 803b
0a:04.3 Class 0805: Texas Instruments Unknown device 803c

I have to disable ACPI Power Management as it is on my laptop in order to get sound. I have to set pci=biosirq in menu.list and noapic as well for my Nvidia card to work. 

I'm not sure if this is an alsa issue or just a general problem with Linux itself. Any help would be appreciated.

I have tried turning down the PCM Volume but the volume is already very low as it is, much lower than on Winblows.

---

### Post by Aramil on 2007-01-07
There is no 100% working solution for the moment unfortunately...Everyone that manages to get sound working has similar problems.But something else I have just figured out....Does your CPU fan working under Ubuntu....?Because I realised that temperatures in Ubuntu are way higher than in XP and I also cant hear any fan working...

---

