---
title: "Reading a DVR Filesystem"
date: 2013-05-21
forum: Multimedia Software
---

### Post by awacs on 2013-05-21
Someone gave me hard disks from a DVR. Fdisk (Ubuntu 8.04) tells me that one partition is ext2 (and it mounts cleanly), but the other is unknown. It seems to be Ext-based, but does not mount with ext2/3. Fsck breaks down with the usual wrong-filesystem errors: can't find superblock, bad inode # in superblock, device busy (although it really isn't), etc. Googling suggests that it may be something called NVRFS with .NVR files, but I don't have a driver for that. :-(

I'm open to suggestions.

---

### Post by MartyBuntu on 2013-05-22
From a DVR? The recordings are likely encrypted.

---

### Post by Mark Phelps on 2013-05-22
DVRs encrypt their filesystems such that, in many cases, they are "married" to the original DVR device that was used to make the recordings.

In addition, some use "proprietary" filesystems that mat look somewhat like standard filesystems, but are not.

The Net is full of folks trying to retrieve their saved videos from external drives that were used with Verizon DVRs -- only to find out that they can't.

---

