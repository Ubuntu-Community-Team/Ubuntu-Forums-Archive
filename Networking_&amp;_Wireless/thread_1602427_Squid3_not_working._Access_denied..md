---
title: "Squid3 not working. Access denied."
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by nitish777 on 2010-10-21
I installed SQUID3 on a Linux machine with two ethernet interfaces (eth0 and eth1). I used the default settings in the squid.conf file and uncommented the two lines ```
acl localnet src 192.168.0.0/16
``` and ```
http_access allow localnet
```eth0 is connected to a router, which provides Internet access. It is  assigned an IP 192.168.1.2 by the router. I manually configured eth1 to  have an IP address 192.168.5.1. It is connected to a switch. Systems  having IP addresses 192.168.5.x are connected to this switch. I ran  these two commands for NAT:
```
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.5.1:3128
``````
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```
But when I try to access internet from a system having IP 192.168.5.2  through the proxy I get an error that says "Access denied".  What is  wrong with my configuration?

---

### Post by SeijiSensei on 2010-10-22
[http://www.lesismore.co.za/squid3.html](http://www.lesismore.co.za/squid3.html) has some helpful hints about setting up transparent squid3 proxies.  A Google search for "squid 3 transparent proxy" brings up lots of pages about this question.

I'd get rid of the iptables rule for eth0 as well.  You just want to push traffic from the internal network through the proxy and leave the traffic on the external interface untouched.

---

