---
title: "Netgear ND520/508 Network File Server"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by zek132 on 2009-01-07
Please help a Ubuntu noob out.

I've just installed Ubuntu 8.10 and have a following problem.

We have Netgear ND520/508 Network File Server which I can locate via Places>Network>Windows Network

This server has a password and is usually mounted under windows like an external drive.

I wondered if it's possible to mount the server under Ubuntu and if so, how?

Thanks in advance.

---

### Post by zek132 on 2009-01-07
I managed to mount the File Server using samba. Now i have another problem.
When i open the mount point using the file manager, i can't seem to access any files. It says error: Access Denied.
However, if i connect via: /usr/bin/smbclient \\\\Server\Public i can use the get command to download. Any ideas?

---

