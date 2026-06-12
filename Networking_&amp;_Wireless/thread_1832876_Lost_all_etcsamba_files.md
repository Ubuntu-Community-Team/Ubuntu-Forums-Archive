---
title: "Lost all /etc/samba files"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by tokyo-joe on 2011-08-25
I had some troubles on samba, so I re-installed it.

After I uninstalled samba, I noticed old /etc/samba folder/files were left, so I deleted all of them. Then I installed samba, however, no /etc/samba files were installed.

How can I generate default samba configuration files??

---

### Post by mhgsys on 2011-08-25
default file is still in /usr/share/samba/smb.conf 
?
:)

then just copy the /usr/share/samba/smb.conf to /etc/samba/smb.conf

```
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
```

---

### Post by tokyo-joe on 2011-08-25
> **mhgsys said:**
> default file is still in /usr/share/samba/smb.conf 
?
:)

then just copy the /usr/share/samba/smb.conf to /etc/samba/smb.conf

```
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
```

Thanks, they are there!
What are files in /user... directory, by the way? Are they just back-ups or user-specific config files?

---

### Post by mhgsys on 2011-08-25
Basically ; 
Data for installed applications that is architecture&#8722;independent and can be shared between systems.

---

### Post by Morbius1 on 2011-08-25
For future reference purposes only:
>  After I uninstalled samba, I noticed old /etc/samba folder/files were  left, so I deleted all of them. Then I installed samba, however, no  /etc/samba files were installed.
/etc/samba/smb.conf does not come from the "samba" package. It comes from the "samba-common" package because smb.conf is used by the samba client as well as the samba server.

---

