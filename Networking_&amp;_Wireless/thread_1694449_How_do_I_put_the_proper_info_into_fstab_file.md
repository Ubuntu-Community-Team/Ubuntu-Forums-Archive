---
title: "How do I put the proper info into fstab file"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by gilch on 2011-02-24
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

### Post by ajgreeny on 2011-02-24
You need to add a line at the bottom in this format
```
UUID=66E53AEC54455DB2 /media/windows/    ntfs-3g        auto,user,rw 0 0
```First find the UUID of your windows partition with ```
sudo blkid
```Then make a folder to mount the partition with ```
sudo mkdir /media/windows
```Finally edit your fstab file with ```
gksudo gedit /etc/fstab
```and, making sure you get the right UUID from the blkid command, add the edited line, as shown above.
Check that all is well with ```
sudo mount -a
```and report back here any error messages that might appear.

If your Windows 7 install has an OS partition and a data partition, I suggest you automount the data one and not the OS; it is much safer that way.

---

### Post by gilch on 2011-03-02
Thanks.

When I ask for sudo blkid,

here is what I get:

gilles@gilles-desktop:~$ sudo blkid
[sudo] password for gilles: 
/dev/sda1: LABEL="System Reserved" UUID="B6148E9C148E5F6D" TYPE="ntfs" 
/dev/sda2: UUID="1810C6B810C69BDE" TYPE="ntfs" 
/dev/sdb1: LABEL="My Book" UUID="40284A46284A3AE4" TYPE="ntfs" 
/dev/sdd1: LABEL="New Volume" UUID="749CFA9D9CFA5956" TYPE="ntfs" 
/dev/sde1: UUID="e38f5fda-68e0-4c47-ae44-03d2d2c8a8ac" TYPE="swap" 
/dev/sde2: UUID="0bf3138d-6d19-49a4-8b15-afa8f162f84d" TYPE="ext4" 
/dev/sde3: UUID="af932d2a-5d11-47fd-a96f-26000dccbedd" TYPE="ext4" 
/dev/sdf1: LABEL="New Volume" UUID="AC56E67156E63BA8" TYPE="ntfs" 
gilles@gilles-desktop:~$ 

???

Gilles

---

