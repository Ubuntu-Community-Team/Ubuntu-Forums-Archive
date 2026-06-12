---
title: "cant write to SMB share when mounted with fstab"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by n1ght28 on 2012-10-21
Anyone good with Fstab, i cant get the share to mount writable,

can write to it when i access through "Connect to server" in Nautilus but i cant write to it  when i fstab mount it.

my fstab entry looks like

//192.168.1.**/public  /media/pi  cifs username=root,password=*******,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0

any ideas

---

