---
title: "USB Mass Storage not automounting?"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2006-11-24
I was very surprised that edgy does not automount a USB mass-storage device, such as my digital camera, on the desktop. KNOPPIX live does this automatically, and I expected edgy would do the same, like inserting a CD in the drive.

What kind of entry do I need to put in /etc/fstab to get this started, and what else is needed to insure that it mounts to the desktop when connected?

Thank you, Johnpipe

johnpipe@linus:~$ lsusb
Bus 001 Device 002: ID 04cb:0165 Fuji Photo Film Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
johnpipe@linus:~$ 


Here is the existing /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb9
UUID=3c35d3cd-a95c-4253-bd4b-d0721ee82999 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0922-00D6  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda10
UUID=04d3d21c-4d2a-11d9-9684-96e1cfe67c85 /media/hda10    ext2    defaults        0       2
# /dev/hda3
UUID=190C-154F  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=1051-18FC  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=36140054-4d2a-11d9-8e7e-f7187293e3d3 /media/hda5     ext2    defaults        0       2
# /dev/hda7
UUID=83e9bcb4-4d2b-11d9-96e8-f3cccd0b72b6 /media/hda7     ext2    defaults        0       2
# /dev/hda8
UUID=092af732-4d2a-11d9-9907-a92a2771f8f3 /media/hda8     ext2    defaults        0       2
# /dev/hda9
UUID=8d525a10-4d29-11d9-81b2-c8a10860abfa /media/hda9     ext2    defaults        0       2
# /dev/hdb5
UUID=7d1ae21e-3fe1-4886-aa62-7af2ca78384b /media/hdb5     ext2    defaults        0       2
# /dev/hdb6
UUID=70223e33-6eda-4958-8605-e1f097d06084 /media/hdb6     ext2    defaults        0       2
# /dev/hdb7
UUID=60c35b5c-a170-11d9-9e9a-a288ed1c0c96 /media/hdb7     ext2    defaults        0       2
# /dev/hdb8
UUID=4655599c-da55-4b8f-b153-f5ee83dcc589 /media/hdb8     ext2    defaults        0       2
# /dev/hda6
UUID=eccba178-9700-476c-a71a-fdb595b4c114 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Phulerock on 2006-11-24
Hi man,

Ubuntu is also easy to use like anothers. In Dapper, usb disk is automatic mounted and show the icon on the desktop, but in Edgy is not (I don't know why).

Let me help you the easy way to connect you usb disk.
Go to Places menu on the top --> Computer 
--- you will see your usbdisk but its stil not mounts, click on this usb icon for active device. Ok, you can access your disk in /media/usbdisk

Command line:
mkdir /media/usb  (any folder you want !)
mount -t vfat /dev/sda1 /media/usb

ok, after this, you can go to /etc/fstab to see how to setup permanent (which device is sda1)

Hope this help.

Any body in Vietnam here ?

---

### Post by dcstar on 2006-11-24
> **Phulerock said:**
> Hi man,

Ubuntu is also easy to use like anothers. In Dapper, usb disk is automatic mounted and show the icon on the desktop, but in Edgy is not (I don't know why).
.......

It may not be Edgy, but the kernel version mixed in with other factors.

I use a 2.6.17 kernel in Dapper and my USB stick mounts fine, but when I try some 2.6.18 kernels I lose this functionality - and a few other people seem to have the same problem.

If you run **dmesg** when you plug in USB devices you will probably see them detected, but the subsequent mount probably does not occur (but you can then manually run a successful mount command.......)

Just out of interest, does anyone see this problem with an Intel CPU?

---

### Post by disturbedsaint on 2006-11-26
> **dcstar said:**
> It may not be Edgy, but the kernel version mixed in with other factors.

I use a 2.6.17 kernel in Dapper and my USB stick mounts fine, but when I try some 2.6.18 kernels I lose this functionality - and a few other people seem to have the same problem.

If you run **dmesg** when you plug in USB devices you will probably see them detected, but the subsequent mount probably does not occur (but you can then manually run a successful mount command.......)

Just out of interest, does anyone see this problem with an Intel CPU?
My Edgy + 2.6.18 kernel behaved the same until today.
I didn't update any packages, just installed a bunch of programs I needed and all of sudden it works again.

So installing something might fix the problem.
Unfortunately I don't know what this something is :/

---

### Post by CujoQuarrel on 2006-12-05
Having troubles here also. When I plug in a USB drive nothing happens. I have no trouble on my other computer running Dapper.

Can't mount it because nothing gets written to the mtab or fstab.

Is their some utility I should be running?

Thanx

---

