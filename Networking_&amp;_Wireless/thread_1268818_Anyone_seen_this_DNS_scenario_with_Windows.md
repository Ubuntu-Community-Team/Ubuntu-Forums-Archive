---
title: "Anyone seen this DNS scenario with Windows?"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by HaroldCo on 2009-09-17
Jaunty 9.04 retrieves IP from Windows DNS and hostname is populated to Windows DNS. Switch and Windows DNS see correct IP and MAC address. Ifconfig looks to have the correct info, e.g. mask, bcast.
 
I can ping IP address, get to internet, etc. Despite hostname being registered, can not ping with fqn. NSLOOKUP fails on IP with timeout.
 
Played with dhcp3 thinking I needed to force fqn or something but Windows DNS registers the machine. Switch and Windows DNS see correct IP and MAC address for the machine.
 
Any suggestion on how to trouble shoot? Thinking its Windows DNS failing to do something or dropping data?

---

