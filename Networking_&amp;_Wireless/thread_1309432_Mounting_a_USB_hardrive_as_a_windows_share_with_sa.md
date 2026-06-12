---
title: "Mounting a USB hardrive as a windows share with samba"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Ozeuss on 2009-11-01
I've been happily accessing a USB hardrive that is connected to a windows computer in my home network, but all of a sudden I'm not able to mount it.
I'm able to mount folders in the drive, but not the root drive folder
my fstab entry is
<code>
//ozlap/maxtor /media/maxtor cifs credentials=/etc/samba/user,noexec,uid=oz 0 0
</code>

and when i try to mount -a, i get:
<code>
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
</code>
I'm using Jaunty.
Oh- and i the drive gets mounted no problem through nautilus's "Network" option

Thank you in advance.

---

### Post by Ozeuss on 2009-11-04
bump?

---

