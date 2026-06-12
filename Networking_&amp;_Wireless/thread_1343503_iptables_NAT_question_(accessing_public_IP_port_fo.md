---
title: "iptables NAT question (accessing public IP port forward from inside)"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by SergeiFranco on 2009-12-01
Hello, here is my question:
I have a webserver on private network behind NAT, port forwarded.
Ideally I want to access [http://mypublicIP/](http://mypublicIP/) from inside of the said NAT private network. Right now all router does is gets me its own config page (basically it treats public IP as same as private IP on the private side).
I am pretty sure it is possible to do with iptables (I can telnet into router and it runs iptables), as my previous router did that out of the box. I am trying to get my head around but I am lost...

The solutions I am not after are the /etc/hosts and dns server, neither of them are suitable for me (otherwise I would not be asking this question).

Your input will be highly appreciated.

---

### Post by SergeiFranco on 2009-12-01
This looks like a solution:
[http://opensimulator.org/wiki/NAT_Loopback_Routers](http://opensimulator.org/wiki/NAT_Loopback_Routers)

---

### Post by SergeiFranco on 2009-12-01
And this:
[http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO-10.html](http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO-10.html)

---

