---
title: "Auto MASQUERADE ?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by crazysexy on 2010-02-17
Hello 
I have Ubuntu Server Router but how i can make this :

-> sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

to start auto after reboot or start server ?!

---

### Post by stripling20 on 2010-02-18
> **crazysexy said:**
> Hello 
I have Ubuntu Server Router but how i can make this :

-> sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

to start auto after reboot or start server ?!
iptables -A POSTROUTING -t nat -j MASQUERADE -s <ip with class >


hope it might be helpful

---

