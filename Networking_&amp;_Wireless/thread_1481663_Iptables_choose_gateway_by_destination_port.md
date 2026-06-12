---
title: "Iptables choose gateway by destination port?"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by rtho782 on 2010-05-12
Hi, and sorry if this is the wrong place!!

I'm setting up a home fileserver running sabnzbd and connected to two different internet connections over the same interface.

eth0 is set up for two public IP addresses each with their own subnet/gateway etc.

I have sabnzbd set up to connect to Astraweb on both port 119 and port 23...

I would like iptables to route all outbound connections on port 119 via gateway #2, and all other internet traffic (including web browsing etc) via gateway #1, allowing be to effectively load balance the connections.....

Unfortunately figuring out WHAT I want to is about the limits of my knowledge/ability, and this plan seems to mean that I need more than the noob friendly tools that I can actually figure out!!

Any help gratefully received!

---

### Post by ilikeyourflannel on 2010-05-12
To qualify my advice: I have zero experience with iptables - but at one time had a CCNA certification, so hopefully this will be of some help.  If my searching was correct something like 

iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp  --dports 119 -j dnat --to-destination [new desination IP]

should work.  Assuming your traffic on port 119 is TCP.  Best of luck.

---

### Post by rtho782 on 2010-05-13
Hmmm.. seems close but wouldn't that change the destination IP rather than the gateway? :/

---

### Post by DGortze380 on 2010-05-13
> **rtho782 said:**
> Hmmm.. seems close but wouldn't that change the destination IP rather than the gateway? :/

The gateway is a essentially just a destination IP.

---

