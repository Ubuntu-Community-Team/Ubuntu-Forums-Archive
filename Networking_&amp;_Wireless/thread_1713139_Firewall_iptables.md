---
title: "Firewall iptables"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by coolburnmx on 2011-03-23
I have a problem

I need to do a captive portal, but, without the packages that already exist, because i have diferent needs, because I'm not gonna give internet to the clients, that why i don't need to put a webpage with user and password, just need that no mather what page they want to search always brings my webpage.

i need to modify the destination ip address from any network call to my dns server and redirect it to an a webpage in the same server.

I already have

[I]sudo iptables -t mangle -A INPUT -p 53 -j DNAT --to-destination 192.168.2.2

[/I]the curious thing is that i tried without the ip address, and the server tells that i need the argument for "*--to-destination", *so, the commands before have a good syntax.

Can someone knows where is the problem? or gave me another solution?[-o<

---

### Post by coolburnmx on 2011-03-23
By the way the error that appears is

"*iptables: No Chain/target/match by that name."*

thanks

---

