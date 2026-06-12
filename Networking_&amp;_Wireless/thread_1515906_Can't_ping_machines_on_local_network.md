---
title: "Can't ping machines on local network"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by vesayth on 2010-06-23
So in an effort to increase the speed of my netbook, I removed Ubuntu and installed Lubuntu on it. 

When I tried to mount my samba share as I normally do, I noticed it wasn't able to connect - mount error(113): No route to host. 

Sensing something fishy, I attempted to ping the machine (both by name and by IP) - Destination Host Unreachable.

The machine I'm trying to connect to is using Ubuntu 10.04 x64. I attempted to ping the other way and it was able to connect to the netbook just fine.

When the netbook was using Ubuntu, it was connecting fine.

My iptables check out ok, but here is the output of iptables -nvL:

```

Chain INPUT (policy ACCEPT 213 packets, 21635 bytes)
 pkts bytes target     prot opt in     out     source          destination


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source          destination


Chain OUTPUT (policy ACCEPT 315 packets, 28211 bytes)
 pkts bytes target     prot opt in     out     source          destination

```

Also I should probably mention that I am able to ping the gateway as well as connect to the internet with no problems.


Does anyone have any ideas what could be wrong? Does lubuntu have some funky firewall built in to it that I can't find? (I've Googled for information on a Lubuntu default firewall and can't find any)

---

### Post by vesayth on 2010-06-23
Well, I solved the problem myself. Turns out to be user error. When I installed Lubuntu on the netbook, I had to use a hardwire connection to activate the wireless drivers, so I took the connection from my server temporarily. When I plugged it back in, I plugged it into the wrong ethernet port, and thus giving my server a dynamic local IP rather than the static one assigned to it.

---

