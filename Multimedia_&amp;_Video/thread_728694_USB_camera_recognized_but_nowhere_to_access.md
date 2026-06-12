---
title: "USB camera recognized but nowhere to access"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by oki-vino on 2008-03-19
Hi! When I plugged in my Sony Cybershot camera for the first time the other day, Ubuntu came up with the transfer wizard and everything was easy. Today I plugged it in and nothing came up. I went to device manager and Sony DSC is listed under the USB controller while the camera is on, and its not listed while the camera is off. There is no desktop icon for the camera, and its not in Computer. 
So basically, ubuntu knows it's there, but I can't find a way to access it or get the pictures transfered.

---

### Post by rishabh on 2008-03-19
You should try manually mounting it. Type the following in a terminal:

```
sudo mkdir /media/camera
```

That makes a folder for you to mount it into.

```
sudo mount /dev/**X** /media/camera
```

Where **X** is the device name of the camera (eg: sda1, sdb, etc)

---

### Post by oki-vino on 2008-03-19
How do I find out the device name? Here is the output of my sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000750e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9000    72292468+   7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c403376

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/dm-0: 74.0 GB, 74039033856 bytes
255 heads, 63 sectors/track, 9001 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        9000    72292468+   7  HPFS/NTFS

Disk /dev/dm-1: 74.0 GB, 74027487744 bytes
255 heads, 63 sectors/track, 8999 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f9ec021

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 64 MB, 64946176 bytes
8 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         990       63340+   1  FAT12
sean@sean-desktop:~$


****EDIT****

desktop:~$ sudo mount /dev/sde /media/DSC
mount: you must specify the filesystem type


thats what happens when I try to mount sde (which I think is the camera) into the folder I created (DSC)


*****EDIT EDIT*****

Ok, I did the same as above but /sde1 instead. It mounted fine into the DSC folder. I want my wife to be able to do this, so I need a way to bring up the transfer wizard that came up the first time I plugged it in. I dont want to have to mount it into a folder every time. Why did the wizard come up the first time but not every time?

---

### Post by kostkon on 2008-03-19
> **oki-vino said:**
> Hi! When I plugged in my Sony Cybershot camera for the first time the other day, Ubuntu came up with the transfer wizard and everything was easy. Today I plugged it in and nothing came up. I went to device manager and Sony DSC is listed under the USB controller while the camera is on, and its not listed while the camera is off. There is no desktop icon for the camera, and its not in Computer. 
So basically, ubuntu knows it's there, but I can't find a way to access it or get the pictures transfered.

Try to use the *import images* option that both *gThumb* and *F-Spot* have and see if it works.

---

### Post by rishabh on 2008-03-19
Go to 
```
System -> Preferences -> Removable Drives and Media
```
and go to the "Cameras" tab. Is the "Import" choice selected?
The associated command should be
```
gnome-volume-manager-gthumb %h
```

---

### Post by oki-vino on 2008-03-19
that is what's under the camera tab...why doesn't it come up when I plug it in? the box is checked...

**EDIT**
I went into gthumb and went to import pictures. It didn't recognize any camera. I dont understand how the device manager can see it but nothing else does

---

### Post by kostkon on 2008-03-20
> **oki-vino said:**
> that is what's under the camera tab...why doesn't it come up when I plug it in? the box is checked...

**EDIT**
I went into gthumb and went to import pictures. It didn't recognize any camera. I dont understand how the device manager can see it but nothing else does

You could go to the your camera's options and check if you have accidentally changed its mode from *PTP* to *USB Mass Storage* device.

---

### Post by oki-vino on 2008-03-20
Thats so wierd..It was in USB mode before and worked. I switched it to PTP and now it works.  *shrug* Who knows..anyways, THANKS Kostkon! you rock!

---

