---
title: "LDAP and file permissions."
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-03-29
I've got an office setup with a server and clients, all running Ubuntu 11.10.  Using ldap auth.  Home directories are mounted on the server.  Also, a data directory is auto-mounted for all to use.

From a working client(I don't know why this one works):

root@hic-05:~# ls -l /data
-rw-rw----  1 root  root   202526 2012-03-29 15:21 Jen.list
-rw-rw----  1 amy  users   415218 2012-03-29 15:56 junk


From a non-working client (almost all clients):

root@hic-02:~# ls -l /data
-rw-rw----  1 4294967294 4294967294 202526 2012-03-29 15:21 Jen.list
-rw-rw----  1 4294967294 4294967294 415218 2012-03-29 15:56 junk

So, on the non-working systems, there's something missing that looks up the ldap user and groups.  But I have yet to find it...  Not even sure why the one client that works in the example above does...

The auto.master etc. are identical on all clients.

---

### Post by lisanels47 on 2012-04-18
Fixed it!  Had to set NEED_IDMAPD=yes


# cat /etc/default/nfs-common
NEED_STATD=
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=

---

