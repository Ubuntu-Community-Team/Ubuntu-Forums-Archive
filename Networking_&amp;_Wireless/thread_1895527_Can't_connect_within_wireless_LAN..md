---
title: "Can't connect within wireless LAN."
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by jdingley on 2011-12-15
I am trying to network between my two home pcs, mainly to ssh. I have a billion wireless router connected to the internet and two ubuntu dell machines, talking wireless.

Both machines have a fresh install of ubuntu 11.10. Both can happily access the web via wireless, and both can happily connect via ssh to each other if connect to the router via cable. What they can't do is ssh each other when connected via wireless.

The problem is broader than ssh, neither pc can ping the other. Error returned is something like: No such host.

When pinging I am specifying ip and I have checked the ips under "Connection Information" one is 192.168.1.1 the other .2.

Any thoughts?

---

### Post by dandnsmith on 2011-12-15
Sounds like a firewalling problem, or the router doesn't do the routing between PCs - you seem to have taken dns out of the equation by using IP addresses.

---

### Post by jdingley on 2011-12-30
Had a holiday now back and ready to get this problem solved.
The problem has slightly changed the second machine's ip has changed to .5 I assume this happened when I was playing around connecting them to the router via cable. The first machine is still .1
Previously, as mentioned, neither machine could ping the other. Interestingly machine two can now ping machine one. But machine one can not ping two. So the problem has half been solved.
Both machines and fresh ubuntu 11.10 installs and I have not knowingly enabled any firewalls. I have looked at my router settings and can not see anything there. The router does have its firewall enabled but I thought that was a wall on the wan side?
Any ideas on how to proceed?

---

