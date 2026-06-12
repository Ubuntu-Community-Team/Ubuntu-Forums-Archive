---
title: "Slow routing"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by jasajona on 2009-05-27
Hello,

I have two Ubuntu 64bit 8.04 LTS servers running on Citrix Xen 5.  These Ubuntu guests use 2.6.24-24-xen kernel.

Guest A is virtual router/firewall for guest B.
B <---> A <--- internet

On guest A there is interface alias. All traffic that comes to that alias (IP address) A is DNAT'ing to B. All traffic that comes from B is masquerading.

Web server is running on guest B. When users from internet access that web server they have to wait for one or more minutes wile simple page is loaded. And that is not just with http also ssh is working very slowly, especially when terminal window is big (sometimes ssh stops responding). If I put guest B directly connected to internet everything is OK.

I checked iptables on guest A many times and I guess that problem is not in iptables. What else could go wrong in this situation?

---

