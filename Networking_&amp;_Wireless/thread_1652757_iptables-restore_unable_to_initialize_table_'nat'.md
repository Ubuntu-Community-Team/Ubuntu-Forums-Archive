---
title: "iptables-restore: unable to initialize table 'nat'"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by sikander3786 on 2010-12-25
Trying to setup transparent proxy via Squid. I am Following this simple guide.

[http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html](http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html)

So while trying to restore iptables-rules, this error pops up.

```
Bad argument `–i'
Error occurred at line: 3

```

Here is the text from the file, I am trying to restore iptables configuration from.

```
*nat

-A PREROUTING –i eth1 –p tcp –m tcp –dport 80 –j DNAT –to-destination 192.168.2.1:3128
-A PREROUTING –i eth1 –p tcp –m tcp –dport 80 –j REDIRECT –to-ports 3128
-A POSTROUTING –s 192.168.2.0/24 –o eth0 –j MASQUERADE

*filter

-A INPUT –i lo –j ACCEPT
-A INPUT –m state –i eth0 –state REALATED,ESTABLISHED –j ACCEPT
-A INPUT eth1 –j ACCEPT
-A INPUT –p tcp –m tcp –dport 22 –j ACCEPT # permit ssh using putty
-A INPUT –p tcp –m tcp –dport 10000 –j ACCEPT # permit webmin access
-A INPUT –j LOG
-A INPUT –j DROP
-A FORWARD –i eth1 –j ACCEPT
-A OUTPUT –o lo –j ACCEPT
-A OUTPUT –o eth1 –j ACCEPT
-A FOWARD –o eth1 –j ACCEPT
-A FORWARD –s 192.168.2.0/24 –o eth0 –j ACCEPT
-A FORWARD –d 192.168.2.0/24 –m state –state ESTABLISHED,REALTED –I eth0 –j ACCEPT
```

Can somebody please figure out what is going wrong?

OS: 64-bit Lucid Lynx.

---

