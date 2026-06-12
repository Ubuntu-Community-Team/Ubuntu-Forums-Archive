---
title: "Character set problems with cifs"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Snorkr on 2010-10-01
I am accessing a samba share on an Buffalo Terastation from 10.04. Mounting the share from the desktop (gvfs) and using smbclient works fine, all characters are displayed correctly. However, when I do a permanent mount all 8-bit characters show up as "?" and I get "invalid encoding" errors from the desktop file manager. I have tried to use iocharset=utf8 and cp850 but with the same results. The line in /etc/fstab is:

```
//192.168.1.65/TeraGeymsla /backup  cifs guest,iocharset=utf8,rw,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
```

Is there a way to find out whar charset smbclient uses when connecting? 

> smbclient //192.168.1.65/TeraGeymsla -d5

displayed among other things

> Substituting charset 'UTF-8' for LOCALE

What could be the problem?

Thanks in advance.
-S

---

