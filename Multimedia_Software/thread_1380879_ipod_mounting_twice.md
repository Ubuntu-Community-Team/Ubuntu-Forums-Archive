---
title: "ipod mounting twice?"
date: 2010-01-14
forum: Multimedia Software
---

### Post by aridus on 2010-01-14
With Kubuntu 9.10 and KDE 4.3.3 and an Ipod 30 GB I have the problem described below. I have searched the many threads that mention ipod mount problems but have not come across my particular problem, hence this new thread.

I recently restored the ipod in Windows (this erases everything and restores it to factory settings). When I plug it into Kubuntu it mounts twice, once with the name Ipod and once with the name MARTIN, the name I gave it on the restore. I can open MARTIN fine. When I attempt to open Ipod I receive this message (I have not reproduced it all):

'An error occurred.... Unknown Failure: mount: wrong fs type, bad option, bad superblock on /dev/sde1... (etc)'

In itself this is not a problem as the ipod is mounted as MARTIN. However, if the ipod is plugged in at either boot or shutdown, the computer freezes and, although gtkpod can access the ipod, Amarok is having problems seeing it properly.

When MARTIN is mounted (automatically, I have not given it a line in fstab) here is the output of cat /etc/mtab

/dev/sde2 /media/MARTIN vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0

and here is the output of sudo fdisk -l

Disk /dev/sde: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Disk identifier: 0x20202020

Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          11       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sde2              11        3707    29222234+   b  W95 FAT32

Does anybody have any ideas? I am presuming at the moment that if I can get the ipod to mount only once the other problems may magicaly disappear..

With grateful thanks

---

### Post by wooddealer on 2010-02-23
I too am having the same problem after setting up my laptop with Ubuntu 9.10.

Rhythmbox seems unaffected by this, but Amarok is very unhappy.

Please share a solution if you find one.

---

