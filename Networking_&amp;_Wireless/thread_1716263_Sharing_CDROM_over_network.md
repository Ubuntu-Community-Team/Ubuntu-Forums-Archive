---
title: "Sharing CDROM over network"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2011-03-28
Hello, I seem to be having difficulties sharing a CDROM... Here is where I am at:

My smb.conf section looks like this
```
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /media/samba
   guest ok = yes

```

My fstab looks like this, (as directed in smb.conf)
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d541b767-3bee-4adf-95ea-4cbf748d0945 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c0b7a9a9-db48-4acd-a4d8-090cd9a1b58b none            swap    sw              0       0
/dev/scd0       /media/samba   iso9660 defaults,noauto,ro,user    0       0 
/dev/sdb1       /shares         ext3  defaults                    0       0

```

I am trying to read the CDROM with a Windows 7 netbook.
My mount folder has the following permissions:
```
dr-xr-xr-x  1 root root 2048 2007-10-10 01:00 samba

```

Any help would be really appreciated!

---

### Post by zoomiest on 2011-03-28
Weird... it is showing the contents of the CDROM now... it works. Did I just have to wait until something was update? Very weird.

---

### Post by K_Light2003 on 2011-03-28
A couple of questions for ya, as I'm new to linux and was about to set up my drive to do the same thing & was going to use this post as a quide. :)


[LIST=1]
[*]Can you swap cd's and read the new one over the network?
[*]Did it effect the boot process if you happen to leave a CD / DVD in the drive.
[/LIST]
I know these maybe basic questions but I'm still learning about all this.

---

