---
title: "Lost  desktop icon for mounted network share"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by akhilbehl on 2010-01-19
hey all,

I have a funny problem, I have suddenly lost the desktop icon (of a hard drive) for a mounted network share. It is funny because, I have other network mounts which share the same server, and there icons are appearing, and this particular share just does not show up with the icon, even if I try mounting it different locations in the filesystem. Any ideas. I really like those cute icons on my desktop.

---

### Post by akhilbehl on 2010-01-19
oh and yeah.. i am getting a text file in place of the icon.

and also i do not use fstab to mount these drives, i use the following command

*sudo smbmount //storage/temp /media/temp -o credentials=/root/.credentials,uid=1000*

as and when i need it to mount this and other drives.

---

