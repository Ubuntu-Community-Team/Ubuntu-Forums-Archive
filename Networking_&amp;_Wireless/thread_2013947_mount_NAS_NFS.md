---
title: "mount NAS NFS"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by limonadovi on 2012-07-01
Hi All,

I have a D-Link DNS 320 NAS and an Ubuntu 12.04 Linux. I want to use the NAS as NFS for data backup. The NAS is configured as:
There is only one HDD in it, its Volume-1 (standard) looks in AjaXplorer as
```
Default Files
+-main
|   sub
+-Recycle Bin
```For test reasons, I've created a file called proba.txt in directory sub.
Under applications, NFS is enabled.

There is one user named 'balazs' in group 'felhasznalo'. It has R/W access for Volume_1 with access methods CIFS and AFP (enabled by default), FTP disabled. Quota disabled (0). Both for group and user, WebDAV is enabled as R/W.

The Ubuntu has a user with same password in the same group as the NAS.
If I try to mount the NFS as
```
mount -t nfs -o rw,hard,intr 192.168.1.101:/mnt/HD/HD_a1/main/sub /media/nas
```it writes
```
mount.nfs: access denied by server while mounting 192.168.1.101:/mnt/HD/HD_a1/main/sub
```I don't see any way of user authentication during mount, altough something is definitely necessary.
What can be the problem?

Thank you in advance: Balazs

---

### Post by luvshines on 2012-07-03
Does this command works for you```

## Run from client terminal
showmount -e <NFS-server-IP>
```

---

### Post by limonadovi on 2012-07-08
Hi All,

I have the solution:
```
chmod 2775 /media/nas/sub 
```
(mount point for NAS)

I used Ajaxplorer application in NAS to create subdir for this NFS. Subdirs created in Ajaxpf are main/sub, both with UMASK 777. Otherwise I couldn't access it.

in /etc/fstab add the line
```
192.168.1.101:/mnt/HD/HD_a2/Ajaxpf/main/sub /media/nas/sub nfs noauto,sync,rw,hard,intr,nfsvers=3,nolock 0 0

```
in /etc/hosts.deny add the line
```
rpcbind: ALL
```

best regards: Balázs

---

