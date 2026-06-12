---
title: "Static IP / DNS Problems"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by DarkMage2303 on 2008-12-06
I'm trying to setup Ubuntu 8.10 so I can use the internet on my Toshiba TE2100.

In System, Preferences, Network Configuration, Auto Eth0 [Edit], IPv4 Settings my method is [Automatic (DHCP Address Only)] and I've typed in my DNS server and the internet still doesn't work.

---

### Post by bp1509 on 2008-12-06
d

---

### Post by DarkMage2303 on 2008-12-06
They are sticking.

---

### Post by bp1509 on 2008-12-06
d

---

### Post by DarkMage2303 on 2008-12-06
I can't ping or go to any websites :(

---

### Post by Buffalo Soldier on 2008-12-06
Can you open a terminal (Applications -> Accessories -> Terminal) and type:

```
cat /etc/resolv.conf
```

It should display DNS servers that you have specified.

---

### Post by DarkMage2303 on 2008-12-06
I managed to fix it by using sudo gedit /etc/network/interfaces and making the appropriate changes for my internet settings.

---

### Post by bp1509 on 2008-12-06
d

---

