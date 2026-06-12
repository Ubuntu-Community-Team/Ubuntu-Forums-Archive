---
title: "Dual Wan Redundancy Question"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by thefix0r on 2011-01-13
Ok, im not interested in load balancing, or failover, or anything that eloborate.

I simply want my box to respond to incoming requests, from the internet, on both wans.

I have them both nat'd, but the outside world can only talk to one at a time, if I manually switch gateways in /etc/network/interfaces.

What I want is simply to have my box respond, I do not want load balance or failover. All the tutorials I have found on the web are elaborate failover or load balancing schemes.

I have yet to find any information on how to do this simple task, that might I add is done natively in windows by simply setting a static ip on both interfaces, as I am doing in linux.

So why wont it allow connections from the internet on both wans? Is it how linux works???

I can accept incoming connections on both wans only from their respective lan and not from the internet on both at once. as I would like.

Just for redundancy

---

