---
title: "wierd nfs issue"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by briermay on 2013-01-20
I'm running dual NAS servers with failover and having an odd nfs issue.
/etc/exports contains
```
/data/export/ 192.168.1.0/255.255.255.0(rw,no_root_squash,no_all_squash,sync)

```all machines have the exact same userids and group ids on some machines I get this:

```
root@web1:/home# ls -l
total 28
drwxr-xr-x 3 jacqueline jacqueline  4096 Jan 17 17:27 jacqueline
drwxr-xr-x 4 root       root        4096 Jan 18 12:51 mod_ruid2-0.9.7
-rw-r--r-- 1 root       root       15937 May 13  2012 mod_ruid2-0.9.7.tar.bz2
```but on others I get this:
```
root@mail:/home# ls -l
total 28
drwxr-xr-x 3 nobody nogroup  4096 Jan 17 17:27 jacqueline
drwxr-xr-x 4 nobody nogroup  4096 Jan 18 12:51 mod_ruid2-0.9.7
-rw-r--r-- 1 nobody nogroup 15937 May 13  2012 mod_ruid2-0.9.7.tar.bz2
```if i check on each machine the user ids match globally and ts driving me nuts

```
root@nas1:/data/export/home# id jacqueline
uid=1000(jacqueline) gid=1000(jacqueline) groups=1000(jacqueline),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare)
root@nas1:/data/export/home#
``````
root@mail:/home# id jacqueline
uid=1000(jacqueline) gid=1000(jacqueline) groups=1000(jacqueline),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare)
root@mail:/home#
``````
root@web1:/home# id jacqueline
uid=1000(jacqueline) gid=1000(jacqueline) groups=1000(jacqueline),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare)
root@web1:/home#
```

---

### Post by arbuntoo on 2013-02-06
Maybe you need to enable idmapd?

---

### Post by effigies on 2013-05-16
Did this ever get resolved? I have an identical problem: servers with identical UIDs/GIDs unable to map them, and squashing to nobody/nogroup.

I've spent all day on this and cannot resolve it.

---

