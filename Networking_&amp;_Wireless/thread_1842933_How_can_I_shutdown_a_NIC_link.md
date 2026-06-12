---
title: "How can I shutdown a NIC link"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by DrMuerte on 2011-09-12
I tried using: ethtool -s eth1 speed 0
but it changes the link to 1000Mbps again.

---

### Post by haqking on 2011-09-12
> **DrMuerte said:**
> I tried using: ethtool -s eth1 speed 0
but it changes the link to 1000Mbps again.


```
sudo ifdown ethx
```where ethx is your adapter such as eth1 or eth0 etc

replace ifdown with ifup to bring it back up

---

### Post by DrMuerte on 2011-09-12
It says:
ifdown: interface eth1 not configured

Well, it has no IP.

But the link is still active.:-k
Using: ethtool eth1
shows that its speed is 1000Mb/s

---

### Post by haqking on 2011-09-12
> **DrMuerte said:**
> It says:
ifdown: interface eth1 not configured

Well, it has no IP.

But the link is still active.:-k
Using: ethtool eth1
shows that its speed is 1000Mb/s

try from the [GUI]("http://www.liberiangeek.net/2010/09/disable-network-interface-ubuntu-10-0410-10-maverick-meerkat/")

or try


```
sudo ifconfig ethx down
```

---

