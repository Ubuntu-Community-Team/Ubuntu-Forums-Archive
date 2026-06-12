---
title: "DVD Media Player Problem"
date: 2009-10-28
forum: Multimedia Software
---

### Post by Ryanism on 2009-10-28
So my LG dn898 has a usb input. Thumb drives work on it, but my ext. HD does not..I heard it will read Fat32 but not NTFS..can this be true? If it is..how do I switch my ext. NTFS to Fat32?

---

### Post by benerivo on 2009-10-28
I'm guessing your 'LG dn898' is some sort of media player attached to a tv - and which case it is possible that it won't read ntfs drives. To change your external drive to FAT32, you should copy all your data that is on it, to another disk, and then install gparted. You can then use gparted to format the external  drive to FAT32. Once you've done this, you can copy your data back to it.

---

### Post by Ryanism on 2009-10-28
I downloaded gparted and all it seems to do is make isos?

---

### Post by Ryanism on 2009-10-29
Any other programs that may convert my external from NTFS to Fat32?

---

### Post by benerivo on 2009-10-29
GParted will do it. If you look at this pic...

[http://stiffold.files.wordpress.com/2009/07/gparted.jpg](http://stiffold.files.wordpress.com/2009/07/gparted.jpg)

It shows the drive in the top right (/dev/sda). The partitioning is laid out graphically by the coloured bar running across the top. You can right click on the partition names, and mount, unmount, format, resize, delete, etc...

---

### Post by Ryanism on 2009-10-29
The gparted I have won't open..notebook flashes instead...

---

### Post by benerivo on 2009-10-29
Plug your external drive in, but don't mount it (or unmount it, if it automounts). Then in a terminal do...```
sudo fdisk -l
```and note the device name for the drive. It will be something like /dev/sdc1 (sda will be your main internal hard drive). Then do...```
sudo fdisk /dev/sdc
```Then type```
sudo mkfs -t vfat /dev/sda1
```I think that should work, but i've only ever formatted through the command line once.

---

