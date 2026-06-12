---
title: "Best way to route internal ip on eth1 to external ip on eth0"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by clgy15 on 2010-12-09
Hey everybody,
Im setting up a server thats connected to a large network. Now my external ip on the network is static and is 10.0.12.15.
What I want is to create a dhcp network using the second port of my box. The first port eth0 goes to my network with the static ip 10.0.12.15 and my second port is connected to a switch with the static ip 192.168.12.1. Now dhcp works fine but none of the boxes that are connected to the internal ip cannot connect to the internet.

Iv tried using squid and manual static ip routes. Im not using network manager or anything cause its a command line server. Im using Arch if that helps. None of my attempts have been successful.
Help Please!

---

### Post by iponeverything on 2010-12-09
Make sure that ip forwarding is turned on and that you are masquerading if your main gateway device does not have a static pointing back to the box for the segment.

---

