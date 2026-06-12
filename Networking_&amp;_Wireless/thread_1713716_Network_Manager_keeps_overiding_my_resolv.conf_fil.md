---
title: "Network Manager keeps overiding my resolv.conf file"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2011-03-24
EDIT:  Never mind.  Got it to behave by removing domain-name and host-name.

In the dhclient.conf I removed domain-name-servers and domain-search.  But Network manager still keeps putting in the search domain of my ISP.  My DNS is 127.0.0.1 which is what I want.

Should I remove domain-name and host-name too.  If it matters, I have an IPv6 tunnel.  I attached my dhclient.conf file.

---

