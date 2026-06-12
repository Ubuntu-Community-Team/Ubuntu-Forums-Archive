---
title: "TTL Value - slow propagation of updated IP"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by P1C0 on 2010-12-29
Hello,

I've set up a domain in dyndns.org with a TTL value of 60 sec and I'm also using openDNS because my ISP's DNS is cr*p.

I have a dynamic IP so I update both dyndns and opendns every 5 min with my new IP (using ddclient)

Everything works well except from the fact that when my IP changes, it takes about an hour for the domain I'm using to map to the new IP. I can see this by doing telnet myDomain in a terminal, it keeps trying to connect to previous IP.

This only seems to be a local issue, since [http://www.downforeveryoneorjustme.com/](http://www.downforeveryoneorjustme.com/) says I'm ok and I can also connect from an external network very fast after a new IP takes place (within 5 minutes).
The problem is that I have this 1 hour delay from inside the LAN.

Could it be that my rooter keeps a cache or sth? ..cause I can't think of anything else.

---

