---
title: "CD Writer not working since install 10.04 netbook"
date: 2010-09-09
forum: Multimedia Software
---

### Post by simplykathy on 2010-09-09
What have I done wrong?  I'm really "noob", but more than willing to learn...

I can't format any cd/rw's since installing ubuntu - found the way to check this through the forums - 

sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=edccbb3d-93cb-4939-b527-003675f7efca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2b1179f1-36b5-4a23-9acb-475173874bce none            swap    sw              0       0

Disk utility shows the cd writer as /dev/sr0,  if that helps...

---

