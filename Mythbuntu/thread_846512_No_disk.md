---
title: "No disk"
date: 2008-07-01
forum: Mythbuntu
---

### Post by mirekU8000 on 2008-07-01
Hi all. Currently I'm using VISTA and XP as dual boot. Today I decided to install mythbuntu so I bought a new disk and connect it via SATA to my motherboard.
Motherboard ABIT AB9 Quad GT, Intel Core 2 Duo E6400, 2GB RAM Geil...
First I started with LIVE CD, and later on with alternate, but in both cases ubuntu is unable to discover my disk. I can normaly use it within the Windows, so there is no problem with it.
I also disconnected other disks (e.g. where are Win installed) and leave only the new one.
I got following error while try to install with LIVE cd (i386)

Buffer I/O  on dev fd0, logical boot 0
ata06.00 revalidation failed (errno=-5)
ata07.00 revalidation failed (errno=-5)

Later on I tried with the alternate CD (also i386) and similar happened (no Buffer I/O error)

ata5.01 revalidation failed (errno=-5) x2
ata6.00 -||-           -||-

In both cases when it comes to disk partition part, there is no disk to choose i.e. it is not possible to continue with the installation.

Does anyone now what coud be the problem here?

Somehow I installed it. After countless attempts it recognized my WD320 GB (alternate CD), and installation finished. I tried later on few times again with alternate or live CD, but the disk hasn't been recognized although I already installed mythbuntu on it.
If I boot from disk, I can see GRUB, counting and than the booting process starts, but at the end I end up in (initramfs), which means it acctually didn't recongize my disk. 
I think, the problem is that mythnuntu doesn't have appropriate drivers for my sata drive. 
Has anyone idea how to fix this issue?

Thanks

---

### Post by mirekU8000 on 2008-07-13
Hi there, I've read somewhere Ubuntu has problems with disk controller. That might be true, because I installed Suse without above mentione errors.
Will that issue be solved with a new release or there is a some way to patch it?

---

