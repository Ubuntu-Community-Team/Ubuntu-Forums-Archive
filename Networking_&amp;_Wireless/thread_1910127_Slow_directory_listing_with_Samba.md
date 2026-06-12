---
title: "Slow directory listing with Samba"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by anto12358 on 2012-01-16
Ubuntu 11.10, samba shipped with it (3.5.11 I guess).

I have some folders containing many files shared  with samba. If I try to access the folder with another device (it's a media  player running Linux), the directory listing is incredibly slow, it  takes about 0.1 s to list each file (i.e. 1000 files=100 seconds). The  monitor shows a steady network activity of 100 KB/s out and 100 KB/s in.
With the exact same devices, network, etc... but the folders shared with Windows, the problem doesn't happen. If vice-versa I access the folder with a Windows machine, the problem doesn't happen either. It seems a linux-to-linux issue :)

The media player (Fantec R2750) runs busybox and uses 'ufsd' for SMB shares:

[http://www.paragon-software.com/ntfs/ufsd.html](http://www.paragon-software.com/ntfs/ufsd.html)

> / # cat /proc/mounts 
[...]
/dev/scsi/host0/bus0/target0/lun0/part1 /tmp/hdd/volumes/HDD1 ufsd rw,nodiratime,nls=utf8,uid=0,gid=0,fmask=0,dmask=0,sparse,force 0 0
[...]


Googling here and there, I've found that someone had issues with small  file transfers and solved them by adding some lines to smb.conf such as:

>     large readwrite = no
   socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
   read raw = yes
   write raw = yes
   oplocks = no
   level2 oplocks = no


I tried various combinations of these, with no luck.

Any idea? If possible I'd like to solve this from the Ubuntu side, I'd like to keep the Fantec OS alone :D

---

### Post by kid1000002000 on 2012-06-21
Anybody find a solution? Having the same issue.

---

