---
title: "Need help configuring samba"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by neon401 on 2009-11-29
Hi there

I'm pulling my hair out trying to successfully configure samba. Let me try to explain my situation;

I want 2 shares, one for the entire ubuntu system with full read+write permissions, but only accessible by the user *media*.

The other share is /mnt/wd ,my external hard drive. I want this to have read only permissions for guests, but still maintain the read+write permission for the *media *user, of course.

This is what I've got so far
```
[global]
    ; General server settings
    netbios name = Media  #this is the name of the computer
    workgroup = Nalum
    security = user

[root]
    path = /
#not sure what to put here

[wd]
path = /mnt/wd
#not sure what to put here
```


All help is greatly appreciated!

---

### Post by Iowan on 2009-11-29
No guarantees... try **write list = media** for the [wd] share, **valid users = media** for [root].

---

