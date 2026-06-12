---
title: "BIND9 refusing some queries"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by k0sh on 2009-12-06
Hi

So this is my situation:

I have two local networks connected with a router:

192.168.1.0/24 -> desktops(.11-.239), DHCP server (.254) and DNS BIND9 server (.244) 

192.168.234.0/24 -> Apache2 server (.128) and SQUID server (.129)

All hosts belong to mydomain.com

The apache server is known by [www.mydomain.com]("http://www.mydomain.com")


With a configuration where there's no proxy server everything works perfectly, DHCP and DNS servers interact the way they should and the DNS server responds correctly to all queries made by client browsers.


When I add the proxy server and make the clients configure their browsers to use it they can only access the local website ([www.mydomain.com]("http://www.mydomain.com")).

From some wireshark captures, I can see that everytime SQUID sends a query to the DNS server refering to a external website it gets a "Refused" answer.

Any idea why this is happening?

This is my squid.conf:

```
http_port 3128
dns_nameservers 192.168.1.244

acl all src 0.0.0.0/0.0.0.0
http_access allow all
```Thank you.


[SOLVED]

Had to explicitly allow recursion to any client on named.conf

---

