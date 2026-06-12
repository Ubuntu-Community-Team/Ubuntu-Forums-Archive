---
title: "Persistance Network Configuration"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by gfk on 2009-03-31
So I got Ubuntu 8.10 and I can't seem to make the ip address that I assigned to my network card to stay after a reboot.  8.10 don't seem to work like previous versions.

Can somebody tell me how to do this?

---

### Post by coutts99 on 2009-03-31
```
sudo nano -w /etc/network/interfaces
```

```
auto lo eth0
iface lo inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx(enter your ip here)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here)
```

---

### Post by gfk on 2009-03-31
thanks

---

