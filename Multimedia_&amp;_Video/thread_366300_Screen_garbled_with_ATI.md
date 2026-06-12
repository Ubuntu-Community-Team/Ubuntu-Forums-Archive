---
title: "Screen garbled with ATI"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by Prestwick on 2007-02-20
Hey guys, trying to install Ubuntu Edgy on a system with: 

An Athlon64 X2 4600+ 
A DFI Lan Party UT RDX200-CF mobo 
An ATI Radeon x850
1GB Corsair XMS DDR Ram
80GB Maxtor USB HDD (with Ubuntu installed) 
Hanns-G HW191D Widescreen LCD Monitor connected via DVI.

After I installed Ubuntu, I tried to set it up to use the ATI fglrx drivers as per the [Radeon guide in the Ubuntu wiki]("https://wiki.ubuntu.com/RadeonDriverHowto?highlight=%28Radeon%29") but when I restart xorg or if I reboot the screen is garbled and I can no longer get to console via ctrl alt, the screen stays garbled with no indication of a command line, however it does not seem to have crashed as I can toggle num lock on and off.

It works when I use the VESA driver but I want to get the ATI drivers working, how do I do that?

---

### Post by masonfoley on 2007-05-06
I had the same issue.  Resolved by following the instructions found here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

