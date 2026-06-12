---
title: "Unable to view external harddrive"
date: 2010-07-03
forum: Mythbuntu
---

### Post by zacharyrs on 2010-07-03
Hi I plug in my external hard drive to my Mythbuntu system and I don't see it anywhere in the File System -> File Manager. What am I doing wrong? Any help would be greatly appreciated.

---

### Post by an0dos on 2010-07-03
> **zacharyrs said:**
> Hi I plug in my external hard drive to my Mythbuntu system and I don't see it anywhere in the File System -> File Manager. What am I doing wrong? Any help would be greatly appreciated.

Open the terminal [or press "alt-F2" and type:

```
sudo fdisk -l
```and post the output here. Please enclose the output in CODE tags.

---

### Post by zacharyrs on 2010-07-03
Ty for your help:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002c3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120499   967904256   83  Linux
/dev/sda2          120499      121602     8855553    5  Extended
/dev/sda5          120499      121602     8855552   82  Linux swap / Solaris

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38914   312571192+  af  HFS / HFS+
zachary@zachary-desktop:~$
```

---

### Post by an0dos on 2010-07-04
> **zacharyrs said:**
> Ty for your help:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002c3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120499   967904256   83  Linux
/dev/sda2          120499      121602     8855553    5  Extended
/dev/sda5          120499      121602     8855552   82  Linux swap / Solaris

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38914   312571192+  af  HFS / HFS+
zachary@zachary-desktop:~$
```

I think your problem may be related to the drive being formatted as HFS. I have not messed with mounting HFS drives, but you should be able to follow the procedures here under the topic "manually mounting":

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

but don't type the "-t vfat" or "-t ntfs" portion since the drive is a hfs+ drive 

i.e.```
sudo mount /dev/sdd1 /media/external 
```Just make sure you create the folder that you're setting as a mount point before trying to mount the drive to it.

If your mythbuntu system is always on, you may want to just attach the external drive to it and share it using samba. It might make things a little less complicated in a mixed-os environment.

---

