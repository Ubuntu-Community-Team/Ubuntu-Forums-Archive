---
title: "Partition name error"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vaskark on 2010-09-21
I currently have 2 partitions that appear on my desktop. The name of one now contains an error. Any idea of how I can fix this? I included a screenshot.
Thanks.

---

### Post by cariboo on 2010-09-22
What does it show up as in Nautilus->Go->Computer?

---

### Post by vaskark on 2010-09-22
It says ... 80 GB Hard Disk: <same error>

---

### Post by JBAlaska on 2010-09-22
Is the drive that's labeled wrong a windows drive (NTFS or FAT)?

If so, it's probably your volume label, although you can change this in Linux to be honest it's much easer to boot windows and change it there.

If not...I dunno....bump I guess:)

---

### Post by vaskark on 2010-09-22
It's my FAT partition.

---

### Post by VMC on 2010-09-22
What does "Disk Utilities - SMART Data" (System>Admin>Disk Utility), say?

---

### Post by vaskark on 2010-09-22
It says my disk is healthy. Also, when I highlight the relevant volume (10 GB FAT partition) and click 'Edit Partition' I'm prevented from altering the label (see attached pics).

---

### Post by cariboo on 2010-09-22
Run gparted as root, you should be able to change the label. Palimpseset is run as a normal user, so you shouldn't be able to change the label.

---

### Post by vaskark on 2010-09-22
> **cariboo907 said:**
> Run gparted as root, you should be able to change the label. Palimpseset is run as a normal user, so you shouldn't be able to change the label.
Tried that. Sorry I didn't mention it sooner. In gparted I can't seem to make any changes - it's mostly greyed out.

---

### Post by cariboo on 2010-09-22
If you're still running a Windows version that needs fat-32, it's probably easier to change the label in Windows, as was stated earlier in the thread.

---

### Post by VMC on 2010-09-22
Too get the correct device do:```
sudo fdisk -l
```

Then change label:

```
sudo tune2fs -L NewLabel /dev/sdaX
```(X being the partition you want changed)

---

### Post by vaskark on 2010-09-22
> **cariboo907 said:**
> If you're still running a Windows version that needs fat-32, it's probably easier to change the label in Windows, as was stated earlier in the thread.
I checked the FAT32 partition from windows ... no label problem.

---

### Post by vaskark on 2010-09-22
> **VMC said:**
> Too get the correct device do:```
sudo fdisk -l
```Then change label:

```
sudo tune2fs -L NewLabel /dev/sdaX
```(X being the partition you want changed)

$: sudo tune2fs -L TEST /dev/sda4
tune2fs 1.41.12 (17-May-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda4
Couldn't find valid filesystem superblock.

---

### Post by cariboo on 2010-09-22
The label may look OK in Windows, but if you can't change it using Ubuntu, there may be something wrong with the partition, due to an unclean shutdown or something.

I have a Windows system in my shop that has a failing hard drive, Vista works OK except that it runs really slooowwww. All my diagnostic disks, blue screened or in the case of Linux based ones wouldn't detect the hard drive. Running chkdsk on reboot solved the problem well enough that I could run Clonezilla, and clone the partitions.

You may be running into the same sort of problem.

---

### Post by VMC on 2010-09-22
*testdisk* might be able to fix this.
 Also try and backup what files you have on the fat partition before trying anything else. If Clonezilla works then you can format the partition. 

What does fsck report: ```
sudo fsck.vfat /dev/sda4
```

---

### Post by mc4man on 2010-09-22
If you want to change the volume label in gparted a couple of things

You don't need to run gparted as root, admin user has permission needed

The partition cannot be mounted - unmount it (remove the lock symbol

---

