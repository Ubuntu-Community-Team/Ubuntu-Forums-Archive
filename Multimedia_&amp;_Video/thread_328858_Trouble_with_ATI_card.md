---
title: "Trouble with ATI card"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by chesman on 2006-12-31
Okay, i just installed Ubuntu yesterday, and have been trying to install drivers and update them to get rid of the choppy scrolling in any window i have open.

When i check the lspci command in bash i get the following output.

> 00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 104c (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation SATA Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


What worries me is that for my VGA and display controller it says unknown device. 

Can someone help me make my viewing smooth?

thanks

Ches

---

### Post by chesman on 2006-12-31
As well, easy ubuntu was reccomended to me to try, so i id, when itry to install the ATI driver trhoguh it i get the following error:

> E: /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.28.8+2.6.17.6-1_i386.deb: trying to overwrite `/usr/sbin/atieventsd', which is also in package fglrx-6-8-0
E: /var/cache/apt/archives/fglrx-control_8.28.8+2.6.17.6-1_i386.deb: trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-6-8-0

---

