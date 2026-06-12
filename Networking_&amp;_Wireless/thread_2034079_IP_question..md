---
title: "IP question."
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by cosmoshell on 2012-07-27
When using a router how does a server from the internet know witch computer its connecting to if the computers are using the same IP? When I look up my IP from two diffrent computers on the same network from a website the IP adress looks exactly the same. Does this mean it cant tell the diffrence without a cookie or something?

---

### Post by hakermania on 2012-07-27
Hm... I don't really know the answer but I guess that the router knows who from the local network requested what, and, when it is given the required answer, then it redirects it to the specific machine.

---

### Post by papibe on 2012-07-27
Hi cosmoshell.

When a local machine request a web page, the router is made aware of the request. Thus when the page is sent from an Internet server, it will be 'routed' to the correct local machine.

The opposite situation is not the same. When the connections is initiated from the Internet, the router won't know what to do. That's why it is necessary specify port forwarding rules for those situations.

I hope that helps a little bit.
Regards.

---

### Post by chili555 on 2012-07-27
> When using a router how does a server from the internet know witch computer its connecting to if the computers are using the same IP? That's the exact purpose of the router: to "route" traffic to and from your local computers to the internet. It's done with a mechanism called network address translation. [http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)>  It has become a common, indispensable feature in routers for home and small-office Internet connections. Most systems using NAT do so in order to enable multiple hosts on a private network to access the Internet using a single public IP address.

---

### Post by cosmoshell on 2012-07-27
Ok its useing diffrent ports. thats what i was looking for, most sites that i looked at just showed browser agent stuff and IP, this threw me off.

---

