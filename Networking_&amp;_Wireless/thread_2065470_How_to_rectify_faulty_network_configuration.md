---
title: "How to rectify faulty network configuration?"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2012-10-02
I connect to internet through modem. Recently I tried to look into the existing configuration but due to mistake, probably started a new pppoe configuration and aborted the process before completion. Can anybody please check from the /etc/network/interfaces given below if two pppoeconf are there and if it is so, how to rectify it?

```

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


```

Thanks.

---

