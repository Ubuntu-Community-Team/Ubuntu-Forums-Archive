---
title: "localhost not found????"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by amb on 2009-03-04
Hi All:
I'm running Ubuntu 8.04 on a system that connects to our office network via DHCP.  
I've written a program that uses BOOST ASIO (ver 1.37.0) to create a UDP socket on the loopback address (127.0.0.1).
When the system is connected to the network all is well.
When I disconnect from the network, BOOST is complaining that it can't resolve the 127.0.0.1 host.  
The error message "Exception: Host not found (authoritative)".  
If I run the command "host localhost" while disconnected, I get the following reply:  "connection timed out, no servers could be reached"
Is there a way to have the system look into my /etc/hosts file first?  Is this in resolv.conf?
THANXS!!!
amb

---

