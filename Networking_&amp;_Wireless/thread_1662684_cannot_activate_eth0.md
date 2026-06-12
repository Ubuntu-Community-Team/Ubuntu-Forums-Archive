---
title: "cannot activate eth0"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by kcfd25 on 2011-01-08
I currently have 2 NIC.  I'm currently connected to eth1 and eth0 is my onboard.  I've been trying to activate it for a while now with no luck.  I keep getting:

justin@ABC:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied


I've tried editing my  /etc/network/interfaces file to several different things I've seen people recommend but still can't get it to work.  The reason I'm trying to activate it is to use a bridge connection.  Thanks.

---

### Post by PatchesTheCaveman on 2011-01-08
You must run that command as superuser.  e.g.
```
sudo ifconfig eth0 up
```

---

