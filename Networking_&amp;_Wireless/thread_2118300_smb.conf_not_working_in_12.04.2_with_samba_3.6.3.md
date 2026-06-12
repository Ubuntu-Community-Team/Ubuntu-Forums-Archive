---
title: "smb.conf not working in 12.04.2 with samba 3.6.3"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by mormonunderpants on 2013-02-20
I have been using the following, completely insecure version of Samba forever and it has served me well for all versions of Samba I've used to date. Toda*y *I installed Ubuntu 12.04.2 opting to install Samba at time of installation. This resulting in Samba 3.6.3 getting installed. The smb.conf I've relied on for years no longer works - I can see the shares from Windows, but I am denied access to even access them. Researched Samba 3.6.3 and I'm finding a lot of bug reports about smb.conf files not working in 3.6.3, but I can't find one that does - esp. an insecure one like I'm used to. Does anybody have any idea how to recreate this functionality in 3.6.3?

```
[global]
workgroup = WORKGROUP
server string = SambaServer
security = share
name resolve order = hosts lmhosts

[web_server]
path = /var/www
force user = my_username
force group = my_username
read only = no
guest ok = yes
```

---

