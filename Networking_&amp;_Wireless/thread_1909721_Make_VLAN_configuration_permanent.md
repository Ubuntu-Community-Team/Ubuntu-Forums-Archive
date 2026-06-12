---
title: "Make VLAN configuration permanent"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by huntkey on 2012-01-15
Hi experts,

This maybe dumb... I can't make my VLANs stay permanent on my ubuntu box by editing /etc/network/interfaces. I use the VLAN interfaces for my Cisco lab. I don't need IPs on them. The commands I use to create them are:

```

sudo vconfig add eth1 101
sudo ifconfig eth1.101 up

```

I put in the following in my /etc/network/interfaces but doesn't help:

```
auto eth1.101
```

when I restart the networking I got this error:

```
Ignoring unknown interface eth1.101=eth1.101.
```

Ideas?

Thanks!

---

### Post by huntkey on 2012-01-16
Any ideas? It's not a very big problem but I still prefer a solution... Can I add the commands in /etc/init.d/rc.local?
Thanks!

---

