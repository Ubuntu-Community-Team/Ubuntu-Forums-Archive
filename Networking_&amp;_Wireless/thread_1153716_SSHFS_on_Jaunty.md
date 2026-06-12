---
title: "SSHFS on Jaunty"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Azyx on 2009-05-09
I wonder how I can get SSHFS client to work with Jaunty?

mkdir /media/media owed by Azyx
I have installed SSHFS.

Have sudo adduser Azyx fuse
But sudo modprobe fuse get: FATAL: Module fuse not found

I can connect to host with SSH, but when I trie with SSHFS I get:
missing host

---

### Post by Iowan on 2009-05-09
Have you seen [this]("https://help.ubuntu.com/community/SSHFS") help page?

---

### Post by Azyx on 2009-05-10
> **Iowan said:**
> Have you seen [this]("https://help.ubuntu.com/community/SSHFS") help page?

Thanx. :)

---

### Post by chmac on 2012-07-08
Not sure what that help page showed you, but I had the same error message "missing host" like so:
```
sshfs user@host /mnt/point
```

It seems that sshfs wants either user and path, or neither, so this works:
```
sshfs user@host: /mnt/point
```

Posting here in case others find this in the future.

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

