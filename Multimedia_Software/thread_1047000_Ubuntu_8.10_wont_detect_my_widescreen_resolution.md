---
title: "Ubuntu 8.10 wont detect my widescreen resolution"
date: 2009-01-22
forum: Multimedia Software
---

### Post by aneslin85 on 2009-01-22
guys,
am using Viewsonic 17" widescreen monitor.
resolution is 1440x900
ubuntu detects this when its booting time. and it works fine.
but when i restart / shutdown. its getting stuck.

the last line says : 
xxxxx xxxxx xxxxx xxxxx    .............[ ok ]
xxxxx xxxxx xxxxx xxxxx    .............[ ok ]
default screen resulotion is 1024x768 ..

then i cant do anything, i need to restart using my power button.

i installed the Ubuntu using Wubi.

How can i solv the problem?

---

### Post by aneslin85 on 2009-02-04
any help guys.......
plssssssssssssssssss

---

### Post by utnubuuser on 2009-02-04
Hi -- have your tried:> sudo dpkg-reconfigure xserver-xorgin a terminal?

and it's probably a good idea to give a bit more info about your system. in terminal:> lspci

---

### Post by utnubuuser on 2009-02-04
You should also check in: System>>Administration>>Hardware Drivers to make sure any driver listed are enabled.

---

### Post by aneslin85 on 2009-02-05
> **utnubuuser said:**
> Hi -- have your tried:in a terminal?

and it's probably a good idea to give a bit more info about your system. in terminal:

Okay, here it is,

```
home@ubuntu:~$ lspci 

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
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
01:01.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
home@ubuntu:~$ 

```

---

### Post by aneslin85 on 2009-02-05
> **utnubuuser said:**
> You should also check in: System>>Administration>>Hardware Drivers to make sure any driver listed are enabled.


yes bro.

and there are 2 drivers listed,

Nvidia accelerated graphics driver ( Version 173 )
Nvidia accelerated graphics driver (Version 177 ) [ Recommended ]

and I already activated the Version 177,

---

