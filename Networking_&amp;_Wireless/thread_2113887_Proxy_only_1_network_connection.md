---
title: "Proxy only 1 network connection"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by UclaGeek on 2013-02-08
Hi, 

I need some help. My system has 2 wired connections and I need to apply a proxy but only to one of them. I know this might be an odd request but I need one of them to be dedicated to this proxy connection and the other to be free for other network traffic. 

I've done a lot of research on the subject and the only thing I've been able to find is how to proxy the entire system. 

I need the card to connect to a socks5 w/auth proxy

my interfaces file is pretty basic. 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```


Is there anyway to do this?

Thanks in advance.

---

