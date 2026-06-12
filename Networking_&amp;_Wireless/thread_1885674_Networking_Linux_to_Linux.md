---
title: "Networking Linux to Linux"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by sladner84 on 2011-11-23
Hey guys I have 2 Linux computers and I am trying to network them  together using samba.. now the problem that I am running into is that on  my laptop the smb.conf is the same as on my desktop.. now on my laptop.  I am able to browse my desktop shared files like I am suppose to.. and  when I run smbtree everything checks out perfect.. .now when I try  smbtree on the desktop I get connection error when trying to connect to  my desktop... but when I use nautilus [smb://10.0.0.6](smb://10.0.0.6)  I am able to browse the shared files on my laptop.. but not through  "Network"  any ideas?... both my machines are running Ubuntu 11.10

---

### Post by JRV on 2011-11-23
Forget samba, try:```
nautilus sftp://HOSTNAME/PATH
```

---

