---
title: "ipv6 auto dns configuration"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Wordan on 2009-10-18
Hi

I'v set up a ipv6 only network using virtualbox. It consists of a router runing ubuntu 9.04 server which provides ipv6 access only to an internal network within virtualbox. I have 3 clients on this internal network. One 9.10 beta desktop two 9.04 servers. The router uses radvd for autoconfiguration of the hosts on the internal ipv6 network

interface eth1 {
 AdvSendAdvert on;
 prefix 2001:470:<etc..>::/64
 {
  AdvOnLink on;
  AdvAutonomous on;
 };
 RDNSS 2001:470:20::2{ };
};

Routing seams to work fine. I can ping IPv6 addresses. I can dig AAAA records when i 'manually' set a ipv6 dns server into resolv.conf on a 9.04 host.

I cant find where to manualy configure a DNS server in 9.10 beta. The network manager applet crashes whenever i try to change anything using it.

But idealy dns should be autoconfigured for the hosts.

So, 2 questions.

How do i manually configure DNS servers in 9.10

And secondly, how can i set up the hosts to get their DNS servers from the router, without looking into DHCPv6. If this is possible.


Thanks

---

### Post by Wordan on 2009-10-19
How do i manually configure DNS in ubuntu 9.10 and what is the best way to autoconfiguring ipv6 DNS information in a small network.

Thanks!

---

