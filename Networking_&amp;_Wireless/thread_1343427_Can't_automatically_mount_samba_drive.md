---
title: "Can't automatically mount samba drive"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Dave.Wynne on 2009-12-01
This is weird,

I've got a mount on an external machine (WinXP) mounted on my server Jackalope, and when I ```
sudo mount -a
``` it mounts the share but after a reboot it does not.
Here is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md1 during installation
UUID=5ae1a302-af10-4c3b-a145-a48141e39be8 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/md2 during installation
UUID=55b66b53-1f12-40ec-8102-b78ab006dc7a /boot           ext3    relatime        0       2
# swap was on /dev/md0 during installation
UUID=d9396d27-7b95-45f4-91d3-39051f920860 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//TITUS/Backup  /srv/backup     cifs iocharset=utf8,credentials=/etc/smbcredentials,gid=1005 0 0
```

Why is it not mounting automatically?

---

### Post by ner0tic on 2009-12-02
> **Dave.Wynne said:**
> This is weird,

I've got a mount on an external machine (WinXP) mounted on my server Jackalope, and when I ```
sudo mount -a
``` it mounts the share but after a reboot it does not.
Here is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md1 during installation
UUID=5ae1a302-af10-4c3b-a145-a48141e39be8 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/md2 during installation
UUID=55b66b53-1f12-40ec-8102-b78ab006dc7a /boot           ext3    relatime        0       2
# swap was on /dev/md0 during installation
UUID=d9396d27-7b95-45f4-91d3-39051f920860 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//TITUS/Backup  /srv/backup     cifs iocharset=utf8,credentials=/etc/smbcredentials,gid=1005 0 0
```

Why is it not mounting automatically?

what happens when you run:
> 
sudo mount -t cifs //TITUS/Backup /srv/backup -o user=[USERNAME_FROM_CRED_FILE]

this should prompt you for the pass. prior to running the mount -a

---

### Post by Dave.Wynne on 2009-12-02
> **ner0tic said:**
> what happens when you run:

this should prompt you for the pass. prior to running the mount -a

I think you misunderstand my problem, I don't understand why my system does not automatically mount the Samba Share at boot time. Is there something wrong with my fstab file that is stopping the automatic mounting?

---

### Post by Dave.Wynne on 2009-12-02
> **Dave.Wynne said:**
> I think you misunderstand my problem, I don't understand why my system does not automatically mount the Samba Share at boot time. Is there something wrong with my fstab file that is stopping the automatic mounting?

I think I've found a work around [https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48)
I'll try it and if successful will mark this thread solved.

---

