---
title: "Trying to add an existing hard drive"
date: 2008-08-20
forum: Mythbuntu
---

### Post by alienluvchild on 2008-08-20
I'm very new to Mythbuntu and have installed it on a system that contains two hard drives. I need to add the second hard drive without formatting and losing the media files that currently reside there.

All the instructions I've found so far would have me format the second drive and I really would prefer not to do that.

The disk was used for media storage for Ubuntu 8.04 up until this point.

Any instruction would be appreciated.

Thanks.

---

### Post by tamoneya on 2008-08-20
well lets get some info about your setup.  This command will tell all the partitions on your harddrives as well as their formatting.```
sudo fdisk -l
```

---

### Post by alienluvchild on 2008-08-21
> **tamoneya said:**
> well lets get some info about your setup.  This command will tell all the partitions on your harddrives as well as their formatting.```
sudo fdisk -l
```

OK, it looks like it sees both. The following is the info I received.

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280
Disk identifier:0xc46e631a

Device Boot     Start     End     Blocks     Id     System
/dev/sda1  *        1    9331   74951226     83     Linux
/dev/sda2        9332    9733    3229065      5     Extended
/dev/sda5        9332    9733    3229033+    82     Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280
Disk identifier: 0x3d853d84

Device Boot     Start     End     Blocks     Id     System
/dev/sdb1           1    9733   78180291      b     W95 FAT32

Thanks again for the help.

---

### Post by alienluvchild on 2008-08-29
Still trying to get this to work with no progress.

I tried to use path in Mythbuntu of /dev/sdb1/

But path is not found.

Any help would be appreciated.

Thanks.

---

### Post by ian dobson on 2008-08-30
Hi,

Before you can use the new drive you need to mount it. 
First create a directory (something like /mnt/videos) this will be your mount point then mount sdb1 to that directory.

Commands:-

mkdir /mnt/videos
mount /dev/sdb1 /mnt/videos

now when you do a "ls /mnt/videos" you should see all the files on your new harddisk.

When that works we can go about getting it to mount automatically when you boot the system.

Regards
Ian Dobson

---

