---
title: "Connecting two unconnected networks"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by cwscribner on 2010-06-24
This is more a general networking question that involves Ubuntu 9.04.

I have an Ubuntu 9.04 install running Nagios Monitoring.  Currently its monitoring devices on its own network(VLAN?).  There is a separate network handling telecom devices that is in no way connected to the network that holds Nagios.  My question is, how do I get Nagios to monitor devices on this separate network.  E.g. how do I make a connection between the two networks so I can get info from the telecom network?

NOTE: This is at a client site and according to them, they have no intention(i.e. refuse to) establish a connection between the two networks.  The idea that my supervisor had was to install a router(owned by our company) that would forward Nagios specific traffic from the telecom network to the network holding Nagios.  Is this a viable option?

---

