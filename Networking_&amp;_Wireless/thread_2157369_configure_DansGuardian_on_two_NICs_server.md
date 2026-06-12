---
title: "configure DansGuardian on two NICs server"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by shafi on 2013-06-25
I have squid3 installed on my server and its working quite fine
I have two NICs installed on the server:

[HTML]eth0: 10.10.10.5
eth1: 192.168.10.1[/HTML]

So I have below iptables rule to redirect all traffic to squid port (3128)

[HTML]iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.10.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
[/HTML]
recently I have installed [DansGuardian]("https://help.ubuntu.com/community/DansGuardian") but according to the guideline I'm not able to configure it with the two NICs.

Can some one help me with the iptables rules how can I have dansguardian in my network? thanks.

---

