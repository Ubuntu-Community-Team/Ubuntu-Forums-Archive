---
title: "Samba permissions help..."
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2009-09-05
Well, here's the situation. I want to setup a directory that is readable by guests, but only writable by people logged in as "administrator". Here is my configuration so far. Right now it doesn't work properly, and no matter who I'm logged in as, I can't write to the directory. I'm new to this stuff, can anyone please tell me what's wrong with my configuration?:

```
[FTP_SERVICE]
path = /media/windows1/Server_Core_Folder/FTP_Services
browseable = yes
comment = share
writable = no
write list = administrator
create mask = 0775
public = yes
guest ok = yes
```

Thanks,

Dillon

---

### Post by ownaginatious on 2009-09-05
Just to provide an update, it appears that when connecting to the share from another Linux machine, there are no problems and I can write when logged in and not when as guest. Mac and Windows machines both experience the inability to write when logged in problem though.

Any ideas anyone?

---

