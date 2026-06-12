---
title: "Network drive w/ NTFS"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by akernan on 2009-02-24
I have Ubuntu 8.04 and using the SC101 driver for linux, [http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/). I have a lot of pix and music on one of my SC101 drives. Is there a way to use this driver with an existing NTFS drive? I followed the Get Started Guide and it has you make a new fs.

Any help would be greatly appreciated, thanks.

---

### Post by Reiger on 2009-02-24
This (from the link you posted) > The resulting storage area is not interoperable with existing Windows clients. sounds ominous.

---

### Post by akernan on 2009-02-24
So I can't use the driver with an existing NTFS drive?

---

### Post by akernan on 2009-02-26
I tried mounting the fs with ntfs-3g get the following error..

NTFS signature is missing.
Failed to mount '/dev/nbd0': Invalid argument
The device '/dev/nbd0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

I've tried ntfsfix and it doesn't work.  I  booted to winblows and ran chkdsk, it was ok.  Winblows recognizes the drive just fine.  I've tried to reformat a drive with ntfs and it doesn't make a difference.

I ran 'fdisk -l /dev/nbd0' and got

Disk /dev/nbd0: 65.4 GB, 65498251264 bytes
255 heads, 63 sectors/track, 7963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x982b4647

     Device Boot      Start         End      Blocks   Id  System
/dev/nbd0p1               1        7962    63954733+   7  HPFS/NTFS

I tried to mount /dev/nbd0p1 and get the following error..

ntfs-3g: Failed to access volume '/dev/nbd0p1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

I typed 'mount.ntfs-3g --help' and it was no help.

Any ideas?

---

### Post by akernan on 2009-02-27
I talked to the maker of the driver and he said to try ntfs-3g.  I should be able to connect to the drives.

---

