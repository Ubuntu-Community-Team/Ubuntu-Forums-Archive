---
title: "will ubuntu 9.04 work with a ATI RV370 (Radeon X300SE)?"
date: 2009-04-24
forum: Multimedia Software
---

### Post by camerong on 2009-04-24
hey all,

I'd like to upgrade from 8.10 to 9.04 but got a message when trying that said I would suffer degradation of video/graphic card quality...

LSPCI OUTPUT so you know what I'm running..:
> cameron@cameron-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)


I'm not an expert, so can anyone tell me if it's possible to upgrade to 9.04, or if I want to.. Is there a work around or something?

thanks,

cameron

---

### Post by markbuntu on 2009-04-24
There is no proprietary driver for you in Jaunty but the open source ati driver should work just fine with the X300, 2D and 3D. ATI has dropped suppport for all RV200-500 cards starting with 9.4 and future drivers for linux and windows.

If you have installed a proprietary driver from ati you should remove it before upgrading.

---

### Post by Renan Decarlo on 2009-04-25
I've got the same video card here, but i've already upgraded with the proprietary driver installed. Now there is not 3D acceleration anymore, and it's not recognizing the right resolution. What should I do? It's a ATI X300 card..

---

### Post by alone9394 on 2009-07-26
i got the same card and is running fine with 9.04 jaunty i got the settings for xorg.conf from this page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  hope this helps

---

