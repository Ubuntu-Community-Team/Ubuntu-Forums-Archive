---
title: "static mount of NFS share"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by ackster on 2010-07-29
I'm trying to add a liine to fstab to mount a share on every boot.  I can mount the share manually using

sudo mount -t nfs 192.168.2.1:/x_machine /mnt/test

I've added the line 

192.168.2.1:/x_machine  /mnt/test  nfs   rw,hard,intr 0 0

to my /etc/fstab file, but it doesn't seem to mount on boot.  What am I missing.  I tried looking in the log files for an error, but couldn't find anything.

Ubuntu 10.04 x64 desktop edition.

Thanks

---

