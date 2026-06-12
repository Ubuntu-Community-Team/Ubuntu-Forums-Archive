---
title: "HDD Partitions no longer in &quot;media&quot; folder"
date: 2012-10-22
forum: Multimedia Software
---

### Post by mlupton on 2012-10-22
Hey everyone, I don't think this is too difficult of an issue to fix, but for some reason after I installed Quantal, my Windows partition is mounting inside of the /media/myname/ folder rather than the /media/ folder. This is causing a lot of problems within my music library because a lot of my songs are stored on my windows partition. I have a general idea of how to change the mount point for an entirely separate drive, but I have no idea how to do it for a partition. Can anyone help me figure out how to mount my windows partition in /media/ instead of /media/myname/?    :confused:

---

### Post by sagarthegreat1 on 2012-10-25
I second this...ubuntu 12.10/ lubuntu 12.10 mounts external drives, windows partitions under <username> folders inside media....this conflicts with xbmc library....is there any way to go back to the traditional mounting system?

---

### Post by mc4man on 2012-10-25
This is the new way under udisks2 (multi-seat support

Easiest would be just to create fstab entry(s) for volumes you want mounted under /media
You can do so manually or use "Disks" app to do so for you. (edit the mount options per partition.
 Disks will default to setting a mountpoint in /mnt, just change to /media & adjust anything else if desired
(pretty much anything is possible - if wanting a name as a mountpoint just don't have a space in name

screen shows a NTFS set to mount to /media/UUID with a display name of store.
(not mounted at startup so can be mounted/unmounted by user permissions

---

### Post by mlupton on 2012-11-02
Excellent! Thanks mc4man, I knew it shouldn't have been too difficult. I'm going to mark this as solved.

---

