---
title: "Networking Problem WWW"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by root2 on 2009-04-11
Hello everyone,

I am having a real difficult time with one of my servers not being reached from the Internet. I have another server within the same network and its accessible from the Internet but for some reason I can get this corrected. 

IPTABLES
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Internally users are able to get to the apache2 service and work on a local site we use to connect with MySQL but I can't get it to allow connections from outside. I can't get any service including ssh from the INternet but once I log into a server that allows me to connect I can reach it internally. I have made all teh necessary changes on the router and tested with another server almost identical in configuration. I can reach the Apache service via port 80 and ssh. Help any advice will be greatly appreciated.

Thank you

---

### Post by root2 on 2009-04-12
No expert advise or help? I can't believe I am stuck in this situation asking for help. Come any advise? I can use the services for this server internally but when I try them from the Internet I cannot access the system. When I say internally I mean the LAN with no problem. 

How can I see if I have any other firewall or restrictions on the server?

Thank you

---

### Post by Iowan on 2009-04-12
The servers are on different boxes? Is the router set up to forward different ports? (port 80 to one machine, port 8080 (or a different port of your choosing) to the second machine?)

---

