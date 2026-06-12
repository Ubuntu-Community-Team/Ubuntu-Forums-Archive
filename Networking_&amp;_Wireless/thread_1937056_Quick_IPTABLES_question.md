---
title: "Quick IPTABLES question"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by NamelessHero on 2012-03-07
Hello, i'm trying to allow connecting only from 1 ip to ubuntu server. Here is my iptables-save:

```

```:INPUT DROP [63:34214]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
-A INPUT -i eth0 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -d 10.3.2.3/32 -i eth0 -p icmp -j ACCEPT
-A FORWARD -i lo -j ACCEPT
-A OUTPUT -o eth0 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -o eth0 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 10.3.1.5/32 -o eth -p icmp -j ACCEPT

10.3.1.5 - is ubuntu server.
10.3.2.3 - my local computer.

Now look at these rows "-A INPUT -d 10.3.2.3/32 -i eth0 -p icmp -j ACCEPT" - "-A OUTPUT -s 10.3.1.5/32 -o eth -p icmp -j ACCEPT" it should let ping 10.3.1.5 server from 10.3.2.3 only. But it doesn't let ping, what am i doing wrong?

---

