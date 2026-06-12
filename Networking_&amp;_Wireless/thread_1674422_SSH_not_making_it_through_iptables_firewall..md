---
title: "SSH not making it through iptables firewall."
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by schapman43 on 2011-01-23
I did some playing around changing up the configuration of my server and now cannot pass traffic through to port 22.  I have since restored everything back to the way it was but am still not able to ssh into the server.

nmap only shows port 80 and 5222 open.  Both ports that I want open. However I am unable to get 22 to pass.

iptables -nL shows
[img]http://www.theprepared.com/images/tech/iptables_nL.PNG[/img]

netstat -an |grep 22 shows
[img]http://www.theprepared.com/images/tech/netstat.PNG[/img]

I've tried clearing the routing table with the following which did no good.  
ip route flush table main

Can somone point me in the right direction?

---

### Post by schapman43 on 2011-01-23
I'm an idiot, please disregard.  The machine I was using to test SSH is behind a firewall that I reconfigured yesterday.  I failed to open port 22 outgoing.

---

