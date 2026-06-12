---
title: "NFS mount remains RO"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by NarsilAnduril on 2011-04-16
Hi,

I think I'm missing something about a very simple config that doesn't work ... help needed !

I want to mount a NFS share between a virtualbox host (NFS server, Ubuntu 10.04) and a guest (NFS client Ubuntu 10.04).

The host has nfs-kernel-server and portmap installed
/etc/exports is
```
/home/virtualbox/disk1  192.168.56.10(rw)
```
Network and mapping is ok, ssh to 192.168.56.10 from host to guest is ok

The guset has nfs-common and portmap installed
Network and mapping is ok, ssh to 192.168.56.1 (host internal IP) from guest to host is ok

When I try a 
```
sudo mount -t nfs -o rw 192.168.56.1:/home/virtualbox/disk1 /mnt/disk 
```
**/mnt/disk is mounted but remains read only**

Could somebody explain me why ?

Thanks

Diego

---

### Post by NarsilAnduril on 2011-04-17
Self answer : don't forget to set rights to 777 on shared folder (on server's side).

---

