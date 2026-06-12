---
title: "Internet forwarding from wlan0 to eth0 with Karmic."
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by clausismus on 2009-12-27
Hi,

I am using Ubuntu Karmic and I'd like to forward the Internet from the Wireless-Lan-Stick (wlan0) to the Ethernet-Adapter (eth0).

How can I achieve this?

---

### Post by puppywhacker on 2009-12-27
To route ip (forward) via two interfaces you have to enable the kernel option
```
sysctl -w net.ipv4.conf.all.forwarding=1
```

To use the internet from one interface and NAT the private network (10.x.y.z or 172.16.x.y or 192.168.x.y) you have to enable masquerading.
```
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

---

