---
title: "Two IPs on one interface"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by OliW on 2009-10-11
I have a server. I currently have two legal IPs that I would like to assign to it.

It came with the first IP already assigned in /etc/networking/ like so:

```
auto eth0
iface eth0 inet static
        address xx.xx.xx.178
        netmask 255.255.255.248
        network xx.xx.xx.176
        broadcast xx.xx.xx.183
        gateway xx.xx.xx.177
        dns-nameservers yy.yy.yy.yy
        post-up ethtool -K eth0 tx off
```

My new IP is xx.xx.xx.179 (the xx.xx.xx is the same each time) and I believe I want that as an alias on the adapter. 

I have googled this but every time I try, if I'm lucky, it just doesn't work. Sometimes it takes out eth0 which is not desired!

I've found a way to quickly enable the alias that does always work:

```
sudo ifconfig eth0:0 xx.xx.xx.179 up
```

But this isn't great if the server restarts without me being there to bring up the second IP (like happened yesterday).

---

### Post by i.r.id10t on 2009-10-11
Easy.. in /etc/network/interfaces add
```

auto eth0:1
iface eth0:1 inet static
        address xx.xx.xx.179
        netmask 255.255.255.248


```

---

### Post by OliW on 2009-10-11
Urgh. That *was* easy... 

I think I missed out the auto line when I tried before. Thanks!

---

