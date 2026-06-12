---
title: "Forward local HTTP requests to remote Proxy with IPTables"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by anthonws on 2010-03-11
Hello,

I would like to know how to configure iptables to redirect all localhost hHTTP traffic to a remote proxy, including DNS requests.

Basically, is it possible to configure iptables to mimic the function of proxy client configuration, i.e http_proxy var in export.

Thanks!

---

### Post by anthonws on 2010-03-11
So,

If I use the following rule:

iptables -t nat -A OUTPUT -p tcp --dport 80 -j DNAT --to-destination PROXYIP:PORT

it works :) But only with direct IP access (google ip for example).

Only problem now is redirecting DNS requests.

How can I achieve this?

Thanks!

---

