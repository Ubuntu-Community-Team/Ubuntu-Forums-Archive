---
title: "/etc/network/interfaces default"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Wolf197 on 2010-02-17
Does anyone know the default for /etc/network/interfaces? I believe I screwed it it up because I can detect my wireless, it just won't allow me to connect to it. The settings in the /etc/network/interfaces are all messed up. I'm running Ubuntu 9.10.

---

### Post by chili555 on 2010-02-18
For a system using Network Manager, the default for */etc/network/interfaces *is:```
auto lo
iface lo inet loopback
```Also, it is doubtful that amendments to *interfaces* will ever work effectively alongside Network Manager.

Is your network encrypted; WEP, WPA or the like? Are you putting the right code in the right place in NM?

---

### Post by i.r.id10t on 2010-02-18
Ditch networkmanager and use wicd instead

---

