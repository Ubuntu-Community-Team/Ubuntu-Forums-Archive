---
title: "replacing portmap with rpcbind"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-05-04
When I want to install rpcbind instead of portmap, apt-get says the nfs-common and nfs-kernel-server will also be removed.
```
root@server:/home/mahmood# apt-get install rpcbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevent-1.4-2 libnfsidmap2 librpcsecgss3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtirpc1
The following packages will be REMOVED:
  nfs-common nfs-kernel-server portmap
The following NEW packages will be installed:
  libtirpc1 rpcbind
0 upgraded, 2 newly installed, 3 to remove and 108 not upgraded.
Need to get 129kB of archives.
After this operation, 831kB disk space will be freed.
Do you want to continue [Y/n]?
```
Is it safe to do that?

---

