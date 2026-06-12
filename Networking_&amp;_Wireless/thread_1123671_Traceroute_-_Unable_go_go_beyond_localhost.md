---
title: "Traceroute - Unable go go beyond localhost"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by root2 on 2009-04-12
Hello guys,

I am having a problem with a server I configured and can't seem to find the problem why I can't go beyond the localhost when using traceroute. I just tried to see why I am unable to go to the Internet using this particular server and checked the traceroute using a public IP and does not go beyond localhost in other words one hop. Can anyone help me with this? The interface is configured with a static IP, network, networkmask, and gateway with the correct IP. I also checked for restrictions on the IPTABLES and there are no rules configured.

Help

---

### Post by root2 on 2009-04-12
Resolved by modifying the route somehow the gateway or the router was incorrectly added via route.

route add default gw then IP address

This solve the problem.
Thanks

---

