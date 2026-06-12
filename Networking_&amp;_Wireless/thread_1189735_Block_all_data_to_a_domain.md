---
title: "Block all data to a domain?"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by clmbngbkng on 2009-06-17
So I'm trying to figure out how to block all data to a domain. I know with iptables you can drop data from a domain but it doesn't last through boot and when you save those rules to a file and reboot it doesnt block all IPs under that domain.

I've read some about Squid but that seems to be more blocking domains from browsing and I don't know if it will block everything. 

Anyways I'm looking for suggestions and anything you can throw out there would be great. Thanks!


EDIT: Or null route data to a domain? How could I make that work for a whole domain instead of just 1 of the IPs? Hosts file?

---

### Post by penguin-power on 2009-06-17
1. how about useing a vlan? [(look / click here)]("http://www.cyberciti.biz/tips/howto-configure-linux-virtual-local-area-network-vlan.html") and also [(look / click here)]("http://www.linuxjournal.com/article/7268")
2. how put a router between you and the other domain and use access lists? [(look / click here)]("http://www.networkclue.com/routing/Cisco/access-lists/index.aspx")

can you give us more info?

w

---

