---
title: "Non-Upnp applications report TCP ports are closed, but hardware firewall is open"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by JohnnyXmas on 2011-02-02
I've tried searching for this, but with so many posts from people who don't know about how to use a hardware firewall (or that they have one) its hard to find one specifically about this issue:

I'm running Ubuntu 10.10, and have done nothing to modify any networking features in any way, aside from the basics of connecting to my wifi access point. When I attempt to run an application such as Transmission, VNC  or Nicotine, they report that the required ports are closed, and will not accept incoming connections, even though I have them opened on my hardware firewall (DD-WRT). If I enable upnp in these applications, they are able to communicate through the ports with no problem. I've confirmed this is an OS (software) issue by booting this same machine into Windows and confirming everything works fine without upnp (I actually had upnp off on the firewall, and only turned it on to troubleshoot this). 

iptables shows that traffic is free to flow in both directions with no restrictions, and netstat -l shows all applicable apps are listening on the correct ports, but canyouseeme.org reports "no route to host" for all of them.

Ideas?

---

