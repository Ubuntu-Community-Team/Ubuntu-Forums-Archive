---
title: "Internet connection failing without manual dhclient"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Repabil on 2009-05-04
Hey,

I'm using a laptop that is connect via network cable to a stationary computer. The stationary computer has got an internet connection, eth1, that I share with my laptop via the stationary's eth0. The stationary's firewall, ufw, i setup to share the connection as described under "ufw Masquerading" in [ the documentation](https://help.ubuntu.com/9.04/serverguide/C/firewall.html). It's all working except that everytime I restart my laptop I have to do```
sudo dhclient eth1
``` on the stationary (either directly on the computer or via ssh or vnc) for internet to be accessible on *either* of the computers. Trying to pinpoint the problem. Any clues?

---

