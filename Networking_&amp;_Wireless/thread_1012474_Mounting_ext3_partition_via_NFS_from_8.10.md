---
title: "Mounting ext3 partition via NFS from 8.10"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by hydrogen18 on 2008-12-15
I've got a box running debian 4.0 r3 with some NFS shares on it. They mount fine from both ubuntu and debian machines which use ext3 as their filesystem for their '/' drives. I've got several machines I use Xubuntu 8.10 on with JFS as the filesystem. When I do mount here is my error
```

ericu@xubuntu-dell-laptop:/sbin$ sudo mount 192.168.12.90:/media/tb/data /mnt/p4debian -t nfs
mount: wrong fs type, bad option, bad superblock on 192.168.12.90:/media/tb/data,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ericu@xubuntu-dell-laptop:/sbin$ 

```

From what im getting, it seems like the OS needs some sort of program to make ext3 look like JFS, akin to the way that ntfs is mounted via a helper program. How do I get such a program and how do I let mount know how to use that program? Thanks for your help.

---

### Post by hydrogen18 on 2008-12-16
Fixed, just needed nfs-common and portmap packages. Would expect those to come default in an OS, but I guess XUbuntu excludes them to try and keep stuff lightweight.

---

