---
title: "NFSv4 squashing UIDs even though I don't want it to..."
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by kpatz on 2009-02-28
I have two Ubuntu boxes, zuul and quattro.  Zuul runs Hardy Desktop and Quattro runs Intrepid Server.

I set up NFS on quattro with the following export (in /etc/exports):

```

/data/backup/zuul       *(insecure,no_subtree_check,no_root_squash,rw,fsid=0)

```

Then, on zuul, I mounted it:

```

kpatz@zuul:~$ sudo mount -t nfs4 quattro:/ /mnt/zuulbackup

```

I then created files on the mounted directory from zuul, from different user ids including root, and when I read them back, they're all mapped to user nobody, group nogroup.  But only when I read them on zuul.  If I view the exported directory on quattro, the UIDs are correct.

Viewed from quattro (NFS server).  The file "heather" was created under user heather on zuul (uid 1001).  The file "root" was created as root.  The other files were created as me (kpatz, same UID/GID on both boxes).
```

kpatz@quattro:/data/backup/zuul$ ls -l
total 16
-rw-r--r-- 1  1001  1002 3 2009-02-28 13:21 heather
-rw-r--r-- 1 root  root  3 2009-02-28 13:20 root
-rw-r--r-- 1 kpatz kpatz 6 2009-02-28 12:20 test
-rw-r--r-- 1 kpatz kpatz 6 2009-02-28 13:19 test2
kpatz@quattro:/data/backup/zuul$

```
(Note, the uid for Heather doesn't exist on Quattro, thus the UID/GID numbers display above).

Viewed from zuul (NFS client).  
```

kpatz@zuul:~$ ls -l /mnt/zuulbackup
total 16
-rw-r--r-- 1 nobody nogroup 3 2009-02-28 13:21 heather
-rw-r--r-- 1 nobody nogroup 3 2009-02-28 13:20 root
-rw-r--r-- 1 nobody nogroup 6 2009-02-28 12:20 test
-rw-r--r-- 1 nobody nogroup 6 2009-02-28 13:19 test2
kpatz@zuul:~$

```

So what this shows is, when creating files over an NFS mount, the UID/GID gets carried over to the server, but when reading them back from the server to the client, they get squashed to "nobody/nogroup".

Any suggestions?  I want the UID/GID to remain unmolested in either direction.

Thanks,
KJP

---

### Post by kpatz on 2009-02-28
Ahh.. figured it out... had to set my domain in /etc/idnetd.conf.

So obvious... NOT... found an obscure post on the web.

---

