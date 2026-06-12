---
title: "ssh into specific computer on home network"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2013-02-10
Previously, I only had one machine on my home network with an ssh tunnel, so when i connected to my home network via ssh from another location, it would automatically connect to the right machine. i( set my router to redirect ssh requests to that computers LAN IP)

Now that I have multiple machines with ssh tunnels on my home network, the connection is refused. (edit: after resetting my ssh/port22 settings on my router, i can connect to the computer whos IP address matches what i set in the router settings)

How do I connect to each of these machines from an outside network now? Do I have to make another port redirection?

by the way, I can still ssh into the machines from within the network using the internal IPs of the machines in question. The problem occurs when I try to connect from an external IP.

---

### Post by ahallubuntu on 2013-02-10
~

---

