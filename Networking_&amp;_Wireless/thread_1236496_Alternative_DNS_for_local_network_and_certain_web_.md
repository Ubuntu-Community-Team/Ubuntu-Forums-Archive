---
title: "Alternative DNS for local network and certain web sites"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by scaat on 2009-08-10
Hello. I know there is a good chance that this has been addressed before, I have searched quite deep but I could not find any thread about this. 

I am living in Turkey and some sites (I know it is unbelieveable but YouTube and geocities among them) are prohibited to visit. It is quite a shame, but this probably is a subject for another discussion. Anyway, Luckily, sites has been blocked by provider's dns server and we are able to get pass the block with using OpenDNS. I am fine until here. 

My problem is starting right at this point. We are using a VPN between two sites and I need redirection from my router to access other site computers, unless I address other site with all IP addresses, which is quite annoying. When I modify the DNS settings with OpenDNS, I lose the redirection from my router in the site 1 or site 2, and even when I address a computer on local site (like Server1 or Term-M04) Open DNS is trying to resolve it among web addresses. 

So my question is; can we setup a local DNS server to forward local network requests to the router and internet requests to the Open DNS? And if so, how I can do that? 

If anyone has any other idea which does not involves setting up a local DNS server, it is fine too. Thanks in advance guys!

---

### Post by Macchi on 2009-08-10
I would look for dbndns and tinydns.org to build a simpler DNS server. 
The Linux Cookbook and  Linux Networking Cookbook by Carla Schroder published by O'Reilly are excellent sources! Google for tutorials or recipes in the area and check Safari online. Sorry, this is not a complete solution, it is only a short hint.

---

### Post by scaat on 2009-08-11
> **Macchi said:**
> I would look for dbndns and tinydns.org to build a simpler DNS server. 
The Linux Cookbook and  Linux Networking Cookbook by Carla Schroder published by O'Reilly are excellent sources! Google for tutorials or recipes in the area and check Safari online. Sorry, this is not a complete solution, it is only a short hint.

Thanks for reply. So, should I understand that, in principle it is possible to install a local DNS server and let it forward certain requests (e.g. local or internet resolving) to certain DNS servers (local router or OpenDNS) ? 

I will look into the sources you mentioned and post back resulst in here. Thanks!

---

