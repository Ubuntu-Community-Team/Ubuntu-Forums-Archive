---
title: "Multiple Internet connections"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by dfme on 2009-03-03
Hello,
I was looking through the forums but I haven't really found any answers which may help with my problem...

so here's the scenario:
I have two Internet connections:
one goes over Ethernet (eth0)
and the other one goes over a mobile phone (ppp0)

I have a virtual machine running and I would like to route all network traffic from the virtual machine to eth0 (company network).
any other outgoing traffic I would like to route through the mobile phone connection.
yes... i would like to avoid the company's evil web-proxy :-\"

i probably need to use iptables for this but maybe you have a better/alternative solution?

cheers!

---

### Post by dfme on 2009-03-06
hmmm... not alot of input here...
let me ask this another way:
how does ubuntu know which interface to use when both interfaces are up and connected to the internet?

---

