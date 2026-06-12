---
title: "Windows shares info"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by BallAquatics on 2011-08-12
If I use Nautilus to share a folder where is the info stored?  It does not show up in my /etc/samba/smb.conf file.  :confused:

It does work for all my Windoze clients though.  :confused::confused::confused:

Dennis

---

### Post by Morbius1 on 2011-08-12
```
/var/lib/samba/usershares
```

This type of Samba share is called Usershare. It works differently that the "Classsic" samba share that exists in smb.conf although the global parameters in smb.conf still have influence over it.

---

### Post by BallAquatics on 2011-08-12
Thanks Morbius1.  I'm really getting into Ubuntu, but just when I think I've figured something out, it throws me a curve like this one... :)

Dennis

---

