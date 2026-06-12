---
title: "Refresh IP of single interface over SSH"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by wesg on 2012-06-15
I just solved a problem with my server by restarting it. The problem was refreshing the IP address from my cable modem, which is connected to eth1. 

Since I could still SSH over the LAN into eth0, is there a better way to refresh the IP on just that single interface? I made the mistake of releasing the IP of both interfaces while connected, and I was locked out. I guess in the future I could use service networking restart but if I can avoid a LAN disconnection, I'd prefer that.

---

### Post by chili555 on 2012-06-15
I assume, since it's a server, the interface details are declared in /etc/network/interfaces. If so, refresh eth1 with:```
sudo ifdown eth1 && sudo ifup eth1
```

---

