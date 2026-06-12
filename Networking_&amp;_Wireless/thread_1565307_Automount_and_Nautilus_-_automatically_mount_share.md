---
title: "Automount and Nautilus - automatically mount share"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by glypto on 2010-08-31
Hi,
I'm using automount/autofs to mount NFS shares from NAS to my Ubuntu desktop. It works quite well. However, to mount NFS share, I have to touch the mount point (e.g. by doing ls or cd from command line). Until that I cannot access/do not see shares from Nautilus.
Strange thing is that once share is automounted, then it automatically reappers in Nautilus even after it is umounted (by timeout or by restarting autofs). After I reboot Ubuntu, I have to touch the share again to see it nautilus.
Is there a way to automatically mount the shares by automount at boot so they appear in Nautilus immediately ?

My auto.master:
/home/myuser/DiskStation    /etc/auto.diskstation

auto.diskstation:
Video     diskstation:/volume1/Video
Music    diskstation:/volume1/Music

---

