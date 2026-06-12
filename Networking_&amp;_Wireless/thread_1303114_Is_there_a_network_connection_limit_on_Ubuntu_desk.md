---
title: "Is there a network connection limit on Ubuntu desktop"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by shumifan50 on 2009-10-27
I am running Ubuntu Desktop 8.04 (I think - downloaded last Sunday). I have a server program (I know I should use the server version) that works fine until the number of connections increase, then it starts refusing connections or they become VERY slow. Is there a limit on the number of connections in the desktop version? Or is there something I can tweak to improve the situation.
It is running on an Intel Atom 330 (Intel D945GCLF2 motherboard). This is using normal ethernet connections, no wifi involved.

---

### Post by sliketymo on 2009-10-27
> **shumifan50 said:**
> I am running Ubuntu Desktop 8.04 (I think - downloaded last Sunday). I have a server program (I know I should use the server version) that works fine until the number of connections increase, then it starts refusing connections or they become VERY slow. Is there a limit on the number of connections in the desktop version? Or is there something I can tweak to improve the situation.
It is running on an Intel Atom 330 (Intel D945GCLF2 motherboard). This is using normal ethernet connections, no wifi involved.

:popcorn:That will probably have more to do with your ISP that than the OS your running,either server or desktop version.

---

### Post by shumifan50 on 2009-10-27
This problem occurs on an internal 100Mbit/s network, so no service provider is involved. When I run the same server application on a 350MIPS, single cpu single board computer(also using a Linux distro), it has no problems on the same network.

---

### Post by shumifan50 on 2009-10-28
The problem has been solved by disabling IP V6 and entering the updating /etc/hosts to reflect the IP I connect from. Now it takes all connections.
I had a second problem where my default gateway was set to one internet router (different from the one that was doing the natting from outside to it). This caused it to be impossible to ping the server from the router that was suposed to expose it to the internet.

SOLUTION: There seems to be no practical limt to the number of connections Ubuntu Desktop can handle.:D:D

---

