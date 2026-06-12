---
title: "samba start"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by kapdani on 2010-12-30
Does anyone know how samba gets started under Ubuntu 10.10?

Before I upgraded, it was in /etc/init.d/samba

/etc/init.d/samba [start stop restart]

I have no clue how to start/stop/restart samba now that I have upgraded to 10.10.

Anybody? 

TIA,

Welshgeek

---

### Post by Paul41 on 2010-12-30
Try

```
sudo restart smbd
sudo stop smbd
sudo start smbd
```

---

### Post by Orbital_sFear on 2011-03-31
I think you mean:

sudo service smbd start
sudo service smbd restart
sudo service smbd stop

-Orbital

---

