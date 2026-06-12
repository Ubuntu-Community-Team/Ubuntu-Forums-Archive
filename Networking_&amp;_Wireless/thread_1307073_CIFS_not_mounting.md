---
title: "CIFS not mounting"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by deathguppie on 2009-10-30
Hey, after upgrading to 9.10 CIFS no longer mounts properly

```
[   22.146766]  CIFS VFS: Error connecting to socket. Aborting operation
[   22.146825]  CIFS VFS: cifs_mount failed w/return code = -101
[   31.535337] r8169: eth0: link up
[   31.535343] r8169: eth0: link up
 
```

I can see that the problem lies in the rc.d scheme but I can't remember which one starts CIFS.

---

### Post by crazycatlady0 on 2009-11-15
I am having this same problem!

---

### Post by dmizer on 2009-11-15
Please post your /etc/fstab line as well as the output of:
```
sudo mount -a
```

---

