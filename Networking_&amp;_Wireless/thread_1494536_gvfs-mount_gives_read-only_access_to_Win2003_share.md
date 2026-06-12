---
title: "gvfs-mount gives read-only access to Win2003 shares"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by will81 on 2010-05-27
I'm trying to integrate some Ubuntu netbooks into our network at school.  Pupils and staff can log on using likewise-open authentication against a Window 2003 domain controller.  Now I just need to mount their home folders.

gvfs-mount smb://SERVER/USERS$/user/folder works but, looking at the server, only mounts the share with read-only access. Mounting the same share as the same user from a Windows machine mounts it with read-write access.

Is there a manual for the gvfs-command?  I tried man gvfs-mount but it said there was no entry.

Thanks in advance.

---

