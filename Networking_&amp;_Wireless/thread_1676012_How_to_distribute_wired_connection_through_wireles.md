---
title: "How to distribute wired connection through wireless"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by AG* on 2011-01-26
I have a wired connection. I want to to distribute it through my wireless card so that other people around can use it. How??
Thanks a lot

---

### Post by pl@yer on 2011-01-26
I think to start you need to enable forwarding.
```

echo 1>/proc/sys/net/ipv4/ip_forward

```
then use iptables to configure forwarding and NAT
```

sudo iptables -A FORWARD -i eth0 -o wlan0 -s (wlan0's IP ) -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

```

I think something like that would work

---

### Post by gordintoronto on 2011-01-26
Issue 19 of Full Circle Magazine: Create a WIFI Access Point.

---

