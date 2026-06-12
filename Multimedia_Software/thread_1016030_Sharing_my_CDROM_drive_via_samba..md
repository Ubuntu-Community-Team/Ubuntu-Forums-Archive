---
title: "Sharing my CDROM drive via samba."
date: 2008-12-19
forum: Multimedia Software
---

### Post by Ankhwatcher on 2008-12-19
I'm trying to share my CDROM drive (as read only) with samba, and it's not working.
I think my cd-drive is mounting to the wrong place, or the commented instructions in smb.conf are out of date.

in smb.conf:
```
# A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Zubuntu's DVD-ROM
   read only = yes
   locking = no
   path = /media/cdrom0
   guest ok = yes

   preexec = /bin/mount /media/cdrom0
   postexec = /bin/umount /media/cdrom0
```

in fstab:
```
/dev/scd0/     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0  	    0
```
in file browser:
[IMG]http://ankh.is-a-geek.com/browser.jpeg[/IMG]

---

