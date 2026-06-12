---
title: "Adding newly installed OS to the existing grub"
date: 2009-09-06
forum: Mythbuntu
---

### Post by roshambembo on 2009-09-06
HELLO ALL.
I have been running Ubuntu as my only OS for a while, but recently decided to test Mythbuntu. I have Ubuntu installed on a 250GB hard drive by itself, a 1 TB for storage of recorded tv and a 160 GB hard drive that I just installed Mythbuntu on. I figured I'd keep my original grub, so I installed Mythbuntu without the bootloader. I did this with full knowledge that I would have to manually add Mythbuntu to the grub, but somehow it didn't even cross my mind that I didn't know how. I have added a Mythbuntu option to /boot/grub/menu.lst but I don't know exactly where to point it for the kernel and such. Any ideas of how I can find such info?

THANKS A BUNCH,
Alex

---

### Post by quixote on 2009-09-07
It should actually be quite easy.  You need to figure out what linux is calling the mythbuntu partition (eg something like /dev/sdb1 for instance).  Then you can point grub to that partition and issue some very simple commands to find the information it needs to boot.  Then you'd append those to /boot/grub/menu.lst

Instructions are here: [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)  Especially the "command line" subsection of that section should give you what I think you're looking for.

---

