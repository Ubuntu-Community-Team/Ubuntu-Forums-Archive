---
title: "Cannot connect to internet via firefox, after ubuntu update."
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by sahasra on 2012-10-17
I have updated ubuntu 12.04LTS. Since then i cannot connect to internet via any browser. I searched in net, using windows on this problem, and i found out, in my etc/resolvconf, there is no original file. base file is empty. 

i added the following to the interfaces in the network.

auto etho
iface etho inet static
address 
netmask
gatewawy
dns-nameservers

I also changed the networkmanger.confd following this article

[http://hardc0l2e.wordpress.com/2012/05/09/ubuntu-12-04-etcresolv-conf-127-0-0-1-implementation-with-dnsmasq/](http://hardc0l2e.wordpress.com/2012/05/09/ubuntu-12-04-etcresolv-conf-127-0-0-1-implementation-with-dnsmasq/)

I cant connect to internet after the changes as well. can anyone guide me, as to what should i do?

---

