---
title: "Winbind question: difference between openSUSE &amp; Ubuntu"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-07-05
I have windows xp and vita, openSUSE 11.1 and Ubuntu 9.04 installed on a  LAN where resources are shared using Samba.

The Samba setup for all Linux machines is the same.

I have edited nsswitch.conf to turn on wins for both machines:```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns
```

On openSUSE I do not need to install the winbind rpm to ping the machines on the LAN by hostname.
On Ubuntu I do need to install the winbind package to ping the machines on the LAN by hostname.

Does anyone know why winbind is important in the Ubuntu case but not the openSUSE case, with respect to pinging by hostname?

Thanks
swerdna

---

### Post by swerdna on 2009-08-14
Bump

---

