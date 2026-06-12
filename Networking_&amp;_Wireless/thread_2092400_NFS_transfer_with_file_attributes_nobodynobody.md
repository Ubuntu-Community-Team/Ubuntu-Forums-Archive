---
title: "NFS transfer with file attributes nobody/nobody"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by xtrailrunner on 2012-12-07
Hello,
I would like to setup my NAS (Debian-based) as a NFS server to backup files from my Ubuntu 12.10 client. Although I have set "no_root_squash" in /etc/exports all copied files end up with user=nobody and group=nogroup on the server.
I would like to have identical usernames and groups on client and server when backing up.

---

### Post by dannyboy79 on 2012-12-07
NFS is very picky when it comes to UID and GID corresponding to username and groupname, they have to be the same on both machines. Whats the users UID on the 12.04 client, most likely 1000. Does your NAS have the same username and is his UID the same?

---

### Post by xtrailrunner on 2012-12-13
UID and GID were fine. It worked when I removed the already transferred file from the NAS drive and started rsync from scratch. The original permission settings were retained and not updated. So it works now. Thanks !

---

