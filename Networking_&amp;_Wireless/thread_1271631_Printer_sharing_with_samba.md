---
title: "Printer sharing with samba"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2009-09-21
So right now I have my samba configuration file security setting set to 'share' rather than 'user' because there are some shared folders there that I would like to be viewable by anyone.

Anyway, by doing this, it appears that all my printers connected to my computer have become public as well. I would prefer if one needed to log into them to be able to use them. Here is the part of my current smb.conf regarding that:

```

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

```

Also, would anyone know perhaps where the settings are for which printers are and aren't shared? I have some network printers I connect to, and Debian (I'm using it with Gnome, so it's very similar to Ubuntu) seems to like and share them again... which is pointless.

Is there a certain configuration file for disabling this?

Thanks,

Dillon

---

