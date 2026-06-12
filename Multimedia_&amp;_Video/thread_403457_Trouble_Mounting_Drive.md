---
title: "Trouble Mounting Drive"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by squiggie on 2007-04-07
I had a nas box go out on my recently and I was running FreeNAS on it. I took the drives out of it and put them into my ubuntu box to se if I could mount them and salvage the data. My problem is I can't seem to mount them. When I try the mount command specifying the ufs filesystem type, it gives me the bad fstype or bad block error. Here is the output of fdisk -l. I'm trying to mount /dev/hdd1 and /dev/hdb1. Can anyone help me mount these drives so I can salvage my data?


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20972826   83  Linux
/dev/sda2            2612        3133     4192965    5  Extended
/dev/sda3            3134        9726    52958272+  83  Linux
/dev/sda5            2612        3133     4192933+  82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          37       18616+  a5  FreeBSD
/dev/hdb2              66       38792    19518408    f  W95 Ext'd (LBA)
/dev/hdb5              66       38792    19518376+  a5  FreeBSD

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       38776    19543072+  a5  FreeBSD

---

