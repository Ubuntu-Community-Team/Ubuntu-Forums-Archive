---
title: "Problem Upgrading Nvidia Drivers"
date: 2010-02-03
forum: Multimedia Software
---

### Post by MongarEric on 2010-02-03
First let me say that I am a complete linux newbie.  Now, on to the problem...

I was following [_this guide_]("http://ubuntuforums.org/showthread.php?t=1125400") to upgrade my Nvidia drivers because I was having problems getting my dual monitor setup to work.  I read several posts about driver problems and everyone usually suggested upgrading to the latest version.

I got to the point following the previously linked to guide where I had to switch to the console before I could continue.  When I tried to switch to console, the screen went mostly black with weird colors around the edges.  

I searched and found several posts saying to look for a file called 'menu.lst'.  This file does not exist on my computer, so I can't open it and remove the term 'splash' like those posts said.

I read another post where someone said to get to console by booting into recovery mode, so I tried that.  I followed the guide to the point where I was ready to install the new drivers.  When I typed in the command to install the new drivers I got an error saying I was trying to install 64 bit drivers on a 32 bit version of Ubuntu.  I downloaded and installed a 64 bit version of Ubuntu.

I have tried searching and cannot find any answers.  I even tried posting in that guide I mentioned, but it has been 2 weeks with no replies so I decided to try a new thread.

I would greatly appreciate any help.

---

### Post by mörgæs on 2010-02-04
I can not give a clear answer, but if you post the results of ```
hwinfo --gfxcard
``` then maybe someone in here can...

---

### Post by mörgæs on 2010-02-04
Besides: 

Menu.lst belongs to Grub, which was part of Ubuntu 9.04. From 9.10 Ubuntu uses Grub2
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by dabl on 2010-02-04
Except for using "gdm" instead of "kdm", and the navigation to "Hardware Drivers", this guidance should work for Ubuntu as well as it does for Kubuntu:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

---

### Post by MongarEric on 2010-02-07
Thanks for the link to the newer guide.  Unfortunately, that guide requires you to hit CTRL-ALT-F1 to get to CLI.  CLI doesn't seem to want to display on my computer.

Here's my results of hwinfo --gfxcard

25: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_400
  Unique ID: VCu0.Atd04FzI_q1
  Parent ID: 3hqH.qNcqIMr0SqF
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 8600 GTS"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0400 "GeForce 8600 GTS"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x0892 
  Revision: 0xa1
  Memory Range: 0xf2000000-0xf2ffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (rw,prefetchable)
  Memory Range: 0xf0000000-0xf1ffffff (rw,non-prefetchable)
  I/O Ports: 0xbc00-0xbc7f (rw)
  Memory Range: 0xf3de0000-0xf3dfffff (ro,prefetchable,disabled)
  IRQ: 10 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000400sv00001462sd00000892bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (PCI bridge)

Primary display adapter: #25

---

