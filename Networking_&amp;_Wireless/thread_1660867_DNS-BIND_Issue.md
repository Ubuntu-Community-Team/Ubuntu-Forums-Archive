---
title: "DNS-BIND Issue"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by arvindm on 2011-01-05
Greetings
I need some help with DNS Bind. We are running v9 and recently I changed the named.conf for conditional forwarding of a zone. We have 4 servers two masters and two
slaves and I did make the changes to named.conf on all 4. Everything worked fine for this domain related to conditional forwarding. After testing completed I had to 
roll back the change means take the conditional forwarding off from all the name servers for this domain. I did changes on same named.conf and on all 4 servers and restarted 
the bind. For some reason master servers are still doing the conditional forwarding for that domain but slaves are working fine and they are sending to root servers for that 
domain. Can you please tell me why masters servers are not doing the same bheaviour but slaves are working fine. 
Thanks-

---

