---
title: "making samba create files with 755 permissions"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by orlox on 2009-05-16
Hi. Im trying to setup a samba server so it creates files and directories with 755 permissions. I have access for the system users to their homes, where they have access to common folders. All users belong to the same group, so I need 755 permissions so the shared files can be edited by any user. This is my share definition:
```

[homes]
   comment = Home Directories
   browseable = no
   create mode = 0755
   force create mode = 0755
   force directory mode = 0755
   read only = no
   create mask = 0755
   directory mask = 0755
   valid users = %S

```
However, with this, the permission on new files keep being set to 0700.

What is going wrong here???

---

### Post by orlox on 2009-05-16
Seems the problem was actually related with my ignorance

755=rwxr-xr-x
666=rw-rw-rw-

So, i'll see if that works as I want it to.

---

