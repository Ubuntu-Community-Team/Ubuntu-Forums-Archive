---
title: "PCI graphics card"
date: 2009-05-17
forum: Multimedia Software
---

### Post by xsilvergs on 2009-05-17
Hi,

I've just upgraded an old and slow PC from Ubuntu 8.10 to 9.04, this went fine but the PC is very slow and a bit poor in the graphics department.

So I've installed a PCI graphics card I had lying around made by Pine.

I am unable to set the resolution any higher than 800X600 in the display settings and the monitor needs to run at 1024x768.

I guess I need to update / install new drivers to get this card to run properly. How do I do that?

For info:

```
tony@VectraUbuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)
01:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
tony@VectraUbuntu:~$ 


```

Thanks for any help

---

### Post by xsilvergs on 2009-05-17
I still cant get it to work. I've tried editing xorg.conf adding 1024x768 but it doesn't appear as an option

---

