---
title: "Unable to share files"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by gigaSproule on 2010-05-17
I cannot, in any way, share files between my Windows 7 and Ubuntu PCs. I have tried everything out there and nothing seems to work. I don't get why! I have samba installed, I have installed the apache2.2 packages and I have checked the network file sharing.

I can create shares with folders and I can see all the windows computers on the network (but can't access any of them).

I cannot view my Ubuntu computer from the Windows computer either.

---

### Post by SlidingHorn on 2010-05-17
In a terminal, run:

```
sudo fdisk -l
```

Find your windows partition (most likely NTFS, if not, ignore me) and enter the following:

```
sudo mount -t ntfs -o nls=utf8,umask=0222 <your/windows/partition*> /media/c
```
*will look something like "dev/hdb1"

If you choose to unmount, do:

```
sudo umount /media/c
```

This will allow you to access your windows partition on ubuntu...I don't really know how to do it the other way around, but I'm sure someone else will be able to help

---

### Post by gigaSproule on 2010-05-17
sudo fdisk -l
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016ffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14d014cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd695d695

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7813ee82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24793   199146496    7  HPFS/NTFS

```

sudo mount -t ntfs -o nls=utf8,umask=0222 <your/windows/partition*> /media/c
returns 'Permission Denied' even though I am logged in as my usual account.

---

### Post by MedianMajik on 2010-06-05
Did you remember to replace the /path/to/windows* part with the actual path to your windows partition?

---

### Post by lateralus01 on 2010-06-05
Slidinghorn seems to think you're trying to share files between partitions on the same computer, but you're trying to share files over the network between an ubuntu client and windows client right?

Samba is your best bet, if the two computers are on the same LAN and have connectivity (you can check this by making sure each computer can ping the other).

you probably have a configuration problem; the best place I've found to configure samba ubuntu is here:

[http://samba.netfirms.com/sambconf.htm#smb](http://samba.netfirms.com/sambconf.htm#smb)

after you've configured the ubuntu PC, type:

net use k: \\ubuntu-computer-ip\share


Lateralus01

---

