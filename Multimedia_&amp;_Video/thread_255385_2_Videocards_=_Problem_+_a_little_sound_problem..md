---
title: "2 Videocards = Problem + a little sound problem."
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by Thanatios on 2006-09-11
Well, let me explain everything first. 

**Video card problem**
I have 2 videocards (1 onboard, and 1 is a NVIDIA RAVE TNT2). My ubuntu uses the onboard videocard as standard. 
The onboard videocard uses pci@01:00.0. while the NVIDIA videocard uses pci@01.0b.0.

Thats because I had a big problem with my videocard before. When it started up I had a xserver error, and so I had to reconfigure stuff using sudo dpkg-reconfigure xserver-xorg. And disable the NVIDIA Videocard in Bios.

But right now, I know what the problem is. (I Guess). And so I want to try to use the sudo dpkg-reconfigure xserver-xorg command, To change the driver from i814 to nv, and at the 4th configuration, change the pci@01:00.0 to pci@01.0b.0.

I just wanted to ask here, if I am doing everything right.
And also, how do I enter pci@01.0b.0 in that configuration. Because right now it says PCI:0:1:0 (That is pci@01.00.0).

**Sound Problem**
Well, whenever I switch with window. Then the sound lags (in totem). Maybe I need to install a newer sound driver? Or any other suggestions?

Thanks in advance

---

