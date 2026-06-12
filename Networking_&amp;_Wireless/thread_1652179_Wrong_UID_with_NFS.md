---
title: "Wrong UID with NFS"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by dargaud on 2010-12-24
Hello all,
I have an odd problem.
I export 3 directories from UbA (64 bits, 10.10) to UbB (32 bits 10.10). User names and userid are the same on both systems. One mounted dir has wrong userids:
```
UbB $ ll /media/
drwxrwxr-x 14 4294967294 4294967294  4096 2010-12-24 16:29 Large1/
drwxr-xr-x  6 dargaud    dargaud     4096 2010-12-23 23:24 Large2/
drwxr-xr-x 12 dargaud    dargaud     4096 2010-05-10 23:22 Large3/

UbB $ cat /proc/mounts 
UbA:/Tera/Large3 /media/Large3 nfs rw,noatime,vers=3,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,timeo=10,retrans=3,sec=sys,mountaddr=192.168.1.2,mountvers=3,mountport=42497,mountproto=udp,addr=192.168.1.2 0 0
UbA:/Tera/Large2 /media/Large2 nfs rw,noatime,vers=3,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,timeo=10,retrans=3,sec=sys,mountaddr=192.168.1.2,mountvers=3,mountport=42497,mountproto=udp,addr=192.168.1.2 0 0
UbA:/Terhalf/Large1 /media/Large1 **nfs4** rw,noatime,vers=4,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,port=0,timeo=10,retrans=3,sec=sys,clientaddr=192.168.1.3,minorversion=0,addr=192.168.1.2 0 0

UbA $ ll /
lrwxrwxrwx   1 root    root    17 2010-10-12 23:30 Tera -> /media/stuff/
drwxr-xr-x  18 root    root  4096 2010-12-21 18:33 Terhalf/

UbA $ ll /Tera/
drwxr-xr-x  8 dargaud dargaud  4096 2010-05-12 14:17 ./
drwxr-xr-x  6 dargaud dargaud  4096 2010-12-23 23:24 Large2/
drwxr-xr-x 12 dargaud dargaud  4096 2010-05-10 23:22 Large3/

UbA $ ll /Terhalf
drwxr-xr-x  18 root    root     4096 2010-12-21 18:33 ./
drwxrwxr-x  14 dargaud dargaud  4096 2010-12-24 16:29 Large1/

UbA $ cat /etc/exports 
/Terhalf/Large1 UbB(rw,no_subtree_check)
/Tera/Large2    UbB(rw,no_subtree_check)
/Tera/Large3    UbB(rw,no_subtree_check)

UbB $ cat /etc/fstab
UbA:/Tera/Large2    /media/Large2   nfs     async,proto=udp,intr,rsize=32768,wsize=32768,timeo=10,noatime   0       0
UbA:/Tera/Large3    /media/Large3   nfs     async,proto=udp,intr,rsize=32768,wsize=32768,timeo=10,noatime   0       0
UbA:/Terhalf/Large1 /media/Large1   nfs     async,proto=udp,intr,rsize=32768,wsize=32768,timeo=10,noatime   0       0

```
Is it because /Terhalf is a drive while /Tera is a symlink ? Why is the former using nfsv4 but not the others ? Is it because /Terhalf is owned by root ?

---

### Post by dargaud on 2010-12-24
Well, aparently adding vers=3 in the fstab solves it. Still, I'm curious as to why there's a difference.

---

