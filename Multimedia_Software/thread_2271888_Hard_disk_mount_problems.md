---
title: "Hard disk mount problems"
date: 2015-04-02
forum: Multimedia Software
---

### Post by Mycroft91 on 2015-04-02
Hi,
I have a dual boot hdd with windows and ubuntu installed on it. I recently connected it to a dishtv set-top box and it a file system which is now not readable on anything other than the set-top box. I have vital information on the disk and would like to recover it before formatting.

I'm attaching the snapshot of fdisk -l :


Partition table entries are not in disk order


Disk /dev/sdb: 500.1 GB, 500107861504 bytes
1 heads, 63 sectors/track, 15504335 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa78b6793


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256   976773165   488386455   8f  Unknown

I tried to mount it as exFAT,ntfs,ext4 to no succes. Any help is appreciated.
Thanks,
Madhukar

---

### Post by SeijiSensei on 2015-04-02
Set-top boxes use proprietary encryption and file systems to prevent copying and "piracy."  You're out of luck I'm afraid.

---

