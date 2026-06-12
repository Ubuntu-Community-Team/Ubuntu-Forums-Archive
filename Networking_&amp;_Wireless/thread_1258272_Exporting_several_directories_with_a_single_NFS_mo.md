---
title: "Exporting several directories with a single NFS mount point"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by NTolerance on 2009-09-04
I'm resurrecting an [old archived thread](http://ubuntuforums.org/showthread.php?t=710339).  I'm running Ubuntu Jaunty with nfs-kernel-server.  I'm attemping to do what's described in that thread, but I can't make it work.  I've got a video directory on the server that's mounted with the bind option to my home directory.  My home directory on the server is exported via NFS.  Here's my /etc/exports file:

```
/home/user 192.168.10.50(rw,root_squash,async,no_subtree_check,fsid=0)
/home/user/video 192.168.10.50(rw,root_squash,async,no_subtree_check,nohide)
```

When I mount /home/user on the client, the video subdirectory is there but contains no data.

---

### Post by NTolerance on 2009-09-09
bump

---

### Post by NTolerance on 2009-09-15
bump

---

### Post by NTolerance on 2009-09-17
bump

---

