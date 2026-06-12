---
title: "Nvidia and desktop freezes"
date: 2005-12-08
forum: Multimedia &amp; Video
---

### Post by pumkinut on 2005-12-08
I recently installed Kubuntu 5.10 on a new AMD Athlon 64 with a Gigabyte Nforce 3 motherboard and a vanilla 6800 video card.  Installation was fine (did x86-32 btw) and I could login fine.  It was then that I started getting the complete system freezes whenever I would try to go to a menu.  I looked on the requisite fora and found a lot of potential workarounds.  So far I've done:

noapic nolapic acpi=off and pci=noacpi in my grub setup

removed powernowd via apt

stoped the apmd and acpid daemons

made the following changes to my xorg.conf file
   1)Commented out DRI and GLcore loading
   2)Option "RenderAccel"  "False" in the Device section
   3)Option "MergedFB"      "off"     in the Device Section
   4)Option "NvAGP"    both "1" and "2"

All of this has led to no real changes.  I then thought I'd update the nvidia drivers, btw when I tried changing from nvidia to nv in my xorg.conf, X failed saying that it couldn't find the nv module.  Do I have to grab it from somewhere?

Anyway, when I tried to install the new nvidia driver (all from a non-X environment) I first had to get the compiler via apt, then make via apt, and then the script complained that I didn't have libc.  Trying to get that via apt failed, where do I need to get it so that I can compile the frigging kernel module?

Thanks in advance for any help.  I'm trying to get away from Fedora because it's becoming so unmanagable, but the whole system freeze/lock issue is really starting to turn me away.

---

### Post by pumkinut on 2005-12-09
Anyone?

---

