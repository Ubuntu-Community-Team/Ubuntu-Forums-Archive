---
title: "Problem with sound card Ubuntu 9.10"
date: 2009-11-05
forum: Multimedia Software
---

### Post by redelek on 2009-11-05
Good morning,  
 Yesterday I installed the new Ubuntu 9.10.  
 I have a problem with sound card I have a laptop HP Compaq NX6310.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express ```
Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```After booting I issue 
```
sudo alsa force-reload
```
Then everything works. 
 Why do not you start your work right away. I read all the threads in the forum, but none helps. You may have some ideas?

[I]Best regards 
Redelek[/I]

---

### Post by negora on 2009-11-05
**redelek:** I'm not sure if your case is the same. I've another sound chipset and after upgrading to 9.10 the sound stopped working. I had to do the same that you do: Reloading ALSA.

However, once I executed "alsamixer" on the command line (thanks to one thread from these forums) I realized that it was because many of the sound channels were set to mute automatically on every start. Have you checked that?

---

### Post by redelek on 2009-11-05
My alsamixer settings are as in the picture

[[IMG]http://img694.imageshack.us/img694/9880/zrzutekranupredelubi.png[/IMG]](http://img694.imageshack.us/i/zrzutekranupredelubi.png/)

---

