---
title: "Internet Connection sharing"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by darkreaction on 2010-05-22
I'm trying to share my wireless connection with my Xbox 360 over lan. Anyone know how to do this?

---

### Post by iponeverything on 2010-05-22
Add this to /etc/rc.local before the exit 0

```

iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Configure the xbox with an ip on the same network as the linux box and point the xbox to it as the default gw.

---

