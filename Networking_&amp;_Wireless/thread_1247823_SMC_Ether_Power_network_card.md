---
title: "SMC Ether Power network card?"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by Dragonsong on 2009-08-23
Hi, I just installed Ubuntu 9.04 on my old computer, which I have some use for. It's got an ancient network card, which is the SMC Ether Power, and simply put, it doesn't work. Ubuntu fails at connecting to the network using the card, which Ubuntu seems to recognize as "Digital Equipment DECchip 21041 [Tulip Pass 3]". Looking at the card, a chip like that seems to exist on it. Would anyone know of some way to get it working?  Thanks in advance!

---

### Post by Dragonsong on 2009-08-23
bump

---

### Post by Dragonsong on 2009-08-24
bump

---

### Post by Dragonsong on 2009-08-24
So, I was taking a look at what could be the issue here. In the log dmesg gave me, I found this:

[   43.727034] eth0: enabling interface
[   43.757957] eth0: set link BNC
[   43.757963] eth0:    mode 0x7ffc0040, sia 0x10c4,0xffffef09,0xfffff7fd,0xffff0006
[   43.757967] eth0:    set mode 0x7ffc0040, set sia 0xef09,0xf7fd,0x6
[   43.766947] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.790525] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   45.458408] eth0: link up, media BNC

That seems to me like Ubuntu is trying to use the card's BNC connector which I don't want. (There's 2 different connectors on the card) Could this be the issue, and how could i fix it?

---

