---
title: "CIFS user credentials on a qNap 209II NAS-disk"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by amalgamas on 2011-03-29
When I use Nautilus to copy files to my NAS-disk they end up with owner "root" and I cannot edit them.  If I copy them back to my PC they have owner <username> and are editable.

My fstab is: //10.0.0.20/Qmultimedia /media/Mmedia  cifs credentials=/root/.smbcreds,directio,iocharset=utf8,noacl,noperm,rw,nobootwait  0  0 

Of course I want my Mmedia mount on the NAS to behave like another disk on my PC; i.e. owner should be <username> and the files should be editable.  Any suggestions how to accomplish this?

---

### Post by andrewc6l on 2011-03-30
Here's a link that might help:

[http://ubuntuforums.org/archive/index.php/t-642148.html](http://ubuntuforums.org/archive/index.php/t-642148.html)

Essentially, you'll need to change the default uid / gid on the NAS, not something you can do in Ubuntu.

---

