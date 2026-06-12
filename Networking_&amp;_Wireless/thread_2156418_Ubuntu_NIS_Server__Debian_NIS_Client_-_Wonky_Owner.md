---
title: "Ubuntu NIS Server / Debian NIS Client - Wonky Ownership"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by Arthemys on 2013-06-21
I seem to have set up NIS server on Ubuntu and a NIS client on Debian that works (mostly). I can authenticate as users that exist on the Ubuntu server, on the Debian box, but NFS mounts seem to have really wonky owners.

Sample of permissions
```
drwxr-xr-x 13 4294967294 4294967294  4096 Apr 17 19:13 backups/
drwxr-xr-x  6 4294967294 4294967294  4096 Jun  8 11:45 images/
drwxrwxr-x  7 4294967294 4294967294  4096 Jun  6 17:42 iso/
```

---

### Post by Arthemys on 2013-06-21
Solved!

Found a few other threads online saying this is an issue with NFS and the version selection in /etc/fstab
I needed to explicitly specify which version of NFS I wanted, and once I remounted I was working fine.

```

leopard:/home   /home   nfs     nfsvers=3       0       0
leopard:/data   /data   nfs     nfsvers=3       0       0
```

---

