---
title: "Myth 8.04 Steps to add 2nd hard drive"
date: 2008-12-22
forum: Mythbuntu
---

### Post by zf3636 on 2008-12-22
Hello I would like some help to format and partition a 2nd SATA drive for my TV Recordings, Music, Videos.etc or any step by step guide which can help me to achieve this thx.

---

### Post by ian dobson on 2008-12-22
Hi,

1) Use fdisk to partition the drive fdisk /dev/sdb
2) Format the drive using mkfs.ext3 -b 4096 /dev/sdb1
3) Mount the drive by editing etc/fstab 
4) In mythtv-setup add the newly added mount to your storage group.

See [http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml) for point 1-3

Regards
Ian Dobson

---

### Post by whosmatt on 2008-12-22
> **zf3636 said:**
> Hello I would like some help to format and partition a 2nd SATA drive for my TV Recordings, Music, Videos.etc or any step by step guide which can help me to achieve this thx.

After partitioning and formatting as above, I would mount the new drive in a temporary spot /media/newdrive or something like that, then copy the contents of /var/lib/mythtv (assuming you use the default location for content) to the new drive:

```
sudo cp -r /var/lib/mythtv/* /media/newdrive
```
 
after confirming that all your data is intact in the new location, remove those same directories from /var/lib/mythtv like this:

```
sudo rm -r /var/lib/mythtv/*
```

then, re-mount the new drive at /var/lib/mythtv and voila, you have a new drive for your content.

that is, assuming you want to use the new drive exclusively for mythtv content.

---

### Post by zf3636 on 2008-12-30
Hi my hard drive does not mount at boot automaticly I have to manually mount the drive, I edited fstab line the following way 
dev/sdb1    /media/storage       ext3       default      0     2 is there any other way to do this thx.

---

### Post by whosmatt on 2008-12-30
> **zf3636 said:**
> Hi my hard drive does not mount at boot automaticly I have to manually mount the drive is there a way to do this thx.
Edit:

sorry i guess i didn't read thoroughly

if that's indeed your entry you want it to read like this:

```
/dev/sdb1   /media/storage ext3 defaults 0  2
```

---

### Post by whosmatt on 2008-12-30
Oh, also you need to make sure that /media/storage exists and is empty

---

