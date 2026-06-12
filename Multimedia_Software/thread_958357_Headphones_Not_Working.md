---
title: "Headphones Not Working"
date: 2008-10-25
forum: Multimedia Software
---

### Post by bogdan_mbe on 2008-10-25
Hello,

I have a Sony Vaio Notebook with a dual boot configuration - Ubuntu 8.04 + Windows Vista. The problem is that, while running Ubuntu, the headphones simply do not work.

I don't know how to describe the problem, i insert them into the right jack I make sure that the volume is turned on, but I don't hear any sound from them. If I try running Vista, they work.

I've been checking some similar threads, but I couldn't find the right answer.

I've read about installing "linux-backports-modules" with the help of synaptic package manager, but there were lots of similar packages... I've tried installing the latest package, restarting the computer, but it doesn't seem to work at all. Hopefully someone could tell me exactly what to install...

By, the way, here is the output of lspci:

_____________________________________________________________________
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD).
_____________________________________________________________________

---

### Post by Pr0biQ on 2008-11-12
Exatly same problem...it seems like my viao doesnt notice that headphones are plugged.Sb should fix that, its really annoying

---

### Post by Convert on 2008-11-13
> **Pr0biQ said:**
> Exatly same problem...it seems like my viao doesnt notice that headphones are plugged.Sb should fix that, its really annoying

I have a Sony Viao with the headphones working.  I fixed mine by adding the following line to the end of the file /etc/modprobe.d/alsa-base:

"options snd-hda-intel model=vaio"

This assumes you have not changed the sound software used by Ubuntu 8.0.4.

Also, Sony is notorious for using different hardware for different models.  I have a VGN-SZ650N/C laptop.

---

