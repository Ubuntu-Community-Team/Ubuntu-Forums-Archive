---
title: "set FAT volume label"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2007-02-19
I have an MP3 player that connects through USB.  Since I have several USB devices, I'd like to set the FAT volume label (which shows up in Nautilus) so I can tell which is which.

The madenning thing is I've done this before but forgot how!

---

### Post by ariel on 2007-06-24
It appears that this can not be done in an easy manner yet, like you can for EXT2/EXT3 partitions (command e2label).

Check this thread:
[http://lists.freedesktop.org/archives/hal/2007-March/007746.html](http://lists.freedesktop.org/archives/hal/2007-March/007746.html)

However, one easy thing you can do is just reformat the partition, and assign the new label when formatting to VFAT (or fat16 or fat12, as applicable to you)

To do this, after unmounting the disk, you can do (assuming your usb disk partition is /dev/sdc1, and formatting to fat32) as follows

```
sudo mkfs.vfat /dev/sdc1 -n eriUsbVfat
```

---

### Post by Slade Winstone on 2007-09-23
Use mtools, check out:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by henriquemaia on 2008-01-03
> **ariel said:**
> It appears that this can not be done in an easy manner yet, like you can for EXT2/EXT3 partitions (command e2label).

Check this thread:
[http://lists.freedesktop.org/archives/hal/2007-March/007746.html](http://lists.freedesktop.org/archives/hal/2007-March/007746.html)

However, one easy thing you can do is just reformat the partition, and assign the new label when formatting to VFAT (or fat16 or fat12, as applicable to you)

To do this, after unmounting the disk, you can do (assuming your usb disk partition is /dev/sdc1, and formatting to fat32) as follows

```
sudo mkfs.vfat /dev/sdc1 -n eriUsbVfat
```

This comes really handy. Thanks a lot.

---

