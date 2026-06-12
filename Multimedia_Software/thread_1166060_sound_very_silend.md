---
title: "sound very silend"
date: 2009-05-21
forum: Multimedia Software
---

### Post by xiano23 on 2009-05-21
hi,
sorry I'm sure there is a thread with the same problem, but I'm sitting in the nowhere in Malawi and need 30min just to open a site so I can not search so much.

my problem is, that the sounds max level is that silend that it took me a day to figur out that there is any sound. I tied all mixers on max and a bit lower ( I read there is often a problem if you put it on max ) but cant get it louder. I just switched to EasyPeasy 1.0 ( Ubuntu 8.10 eee) befor I had Fedora 8 on my aspire one zg5 and the sond was working fine. 
THX for the help

P.S. I kow just the Basics of linx so pleas step by step. oh and my connection is realy bad so if posible aviod big downloads or bedder all

hardwar info sound:

xiano@xiano-laptop:~$ hwinfo --sound
22: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.ZuLf8A1rLm6
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x015b 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x58540000-0x58543fff (rw,non-prefetchable)
  IRQ: 16 (71648 events)
  Module Alias: "pci:v00008086d000027D8sv00001025sd0000015Bbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by dabl on 2009-05-21
There are many, many tips in this thread to fix sound issues:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


and tips here for Intel sound options:

[http://ubuntuforums.org/showthread.php?t=1043568&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=1043568&highlight=snd_hda_intel)

---

