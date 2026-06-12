---
title: "smb.conf file - problems with permissions of created file in samba share"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-09-18
Hi,
I would like any file created or transferred to my samba share to have permissions of 770 i.e rwxrwx---. The permissions of the samba share directory are set to 777. I have tried adding the " create mode = 0770" but I when I put or create a file in the share the file's permissions are 760.

```
[samba]

path= /home/samba
read only = no
 guest ok = yes
 create mode = 0770

```

I have also added "force directory mode = 770" but also to no avail.

Any help would be appreciated.

C

[solved]

Elementary mistakes, should be :
```

[samba]

path= /home/samba
read only = no
 guest ok = yes
 create mask = 0770
 force create mode = 0770

```

---

