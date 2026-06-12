---
title: "how to refresh network after power failure on laptop"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by jives11 on 2010-04-24
Hi, I have Karmic Coala runing on an IBM thinkpad X.41. Works great. My home network is all ethernet so I have a router , CAT5 cable to laptop.

A couple of times I've had power outages. The laptop carries on as it's on battery power. When the power comes back , the router restarts, it reconnects after a few minutes but the laptop doesn't reconnect to the network seamlessly. On some other Linux distro's I've had running /etc/init.d/network restart will refresh everything. On Ubuntu I have /etc/init.d/networks but running restart on this didn't seem to help. In the end I needed to reboot the laptop to get the network back on. Perhaps this is a power management issue with the laptop ethernet card i.e losing power powers down the card and it never comes back up properly.

Anyhow any advice or suggestions gratefully received

---

### Post by x1a4 on 2010-04-24
Hi,

Try
```
sudo ifdown *eth0* 
sudo ifup *eth0*
```

Where *eth0* is the name of your net interface.

---

### Post by NichoTL on 2010-04-24
How about:
```
sudo restart network-manager
```

---

