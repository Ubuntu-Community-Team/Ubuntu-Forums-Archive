---
title: "Upgrade 8.04 t0 8.10 problem"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by timmson on 2008-12-16
Hello
After upgrading from hardy to intrepid i found some problem. Network-manager applet shows that wire network is not connected. But network is up.What is problem?

---

### Post by Kobalt on 2008-12-16
Hello,

Do you use a custom /etc/network/interfaces file? Is it edited? If you're unsure, please post the output of (remove any credential entries such as WPA key if present) : ```
cat /etc/network/interfaces
```

---

### Post by timmson on 2008-12-16
thanx
this file:
auto lo
iface lo inet loopback


iface eth0 inet static
address 172.16.1.5
netmask 255.255.252.0
gateway 172.16.3.57

auto eth0

---

### Post by albinootje on 2008-12-16
> **timmson said:**
> thanx
this file:
auto lo
iface lo inet loopback


iface eth0 inet static
address 172.16.1.5
netmask 255.255.252.0
gateway 172.16.3.57

auto eth0

If you want you can remove the whole eth0, the result will be :

auto lo
iface lo inet loopback

After that try again to see whether Network-manager likes it :)

---

### Post by timmson on 2008-12-16
if i do this changhes, my IP will get from DHCP server, not static?

---

### Post by albinootje on 2008-12-16
> **timmson said:**
> if i do this changhes, my IP will get from DHCP server, not static?

That depends on your settings in Network-manager.
Default in NM is roaming i think, which will use dhcp.
But you can also make Network-manager produce a static ip for you.

---

### Post by timmson on 2008-12-16
ok, big thnx. i'll try it

---

