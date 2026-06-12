---
title: "Mount @ Boot / fstab Permissions"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by Socratez on 2009-11-24
I am trying to mount a remote Samba share to my /data/Music folder when the system boots. I have managed to do this but now all the files are showing permissions for '502 - user #502' and I cannot read/write these files. 

Any help with this would be appreciated. If it helps I have it mapped to a NSLU2 share with full R/W Permissions for all users (mountd included) Here is the fstab line for the mount at boot

//192.168.1.190/music /data/Music cifs auto,username=mountd,password=************,fmask=0777,dmask=0777 0 0

---

### Post by Lord_ on 2009-11-24
Hi,

Try adding " rw" after the auto. I this should mount it for read and write permissions.

---

### Post by Lord_ on 2009-11-24
I think you can also get rid of the ,fmask=0 777,dmask=0777 part

---

### Post by Socratez on 2009-11-24
//192.168.1.190/music /data/Music cifs auto rw,username=mountd,password=************, 0 0

When I run a sudo mount -a

[mntent]: line 19 in /etc/fstab is bad

Maybe there is something wrong in the FSTAB itself?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=996c125e-fb8b-4850-9c3b-fc3e08f01ea6 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sdb1 during installation
UUID=57910dc6-f041-4420-9f18-6397428b87ed /data           reiserfs defaults        0       2
# /home was on /dev/sda2 during installation
UUID=231942b0-d7e4-47f4-b216-574791916bd5 /home           ext4    defaults        0       2
# /vOS was on /dev/sda3 during installation
UUID=0a895fdd-a1a7-4590-ac35-7b7ed7891efe /vOS            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ef3c0c78-96d9-4410-b093-093aaad2ac50 none            swap    sw              0       0
//192.168.1.190/music /data/Music cifs auto rw,username=mountd,password=******** 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

