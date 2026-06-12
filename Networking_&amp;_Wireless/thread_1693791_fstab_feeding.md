---
title: "fstab feeding"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by gilch on 2011-02-23
I have a working network Ubuntu 10 Win7 (thanks to you guys on this site).

My last hurdle is how to mount folders or disks from Win7 onto Ubuntu.

I used a tutorial, and got fstab installed I think...

Where do I get the information to PUT IN fstab and WHERE to put it? (please don't laugh) (Thanks).

Here is my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=0bf3138d-6d19-49a4-8b15-afa8f162f84d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=af932d2a-5d11-47fd-a96f-26000dccbedd /home           ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=e38f5fda-68e0-4c47-ae44-03d2d2c8a8ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//servername/sharename  /media/shares  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0


Gilles

---

