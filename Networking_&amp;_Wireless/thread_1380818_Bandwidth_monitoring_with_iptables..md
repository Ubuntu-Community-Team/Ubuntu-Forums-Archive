---
title: "Bandwidth monitoring with iptables."
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by hans-jakob on 2010-01-14
I have set up a mumble-server width 10 virtual servers (port 64738 to 64747), and I want to monitor the bandwidth use of every virtual server. I thought that iptables would possibly be a good idea, but I have doubts whether it is set up properly.

I have iptables set up as follows:

iptables -N mumble
iptables -I INPUT -p tcp --dport 64738:64747 -j mumble
iptables -I INPUT -p udp --dport 64738:64747 -j mumble
iptables -A mumble -p tcp --dport 64738 -j ACCEPT
iptables -A mumble -p udp --dport 64738 -j ACCEPT
iptables -A mumble -p tcp --dport 64739 -j ACCEPT
iptables -A mumble -p udp --dport 64739 -j ACCEPT
iptables -A mumble -p tcp --dport 64740 -j ACCEPT
iptables -A mumble -p udp --dport 64740 -j ACCEPT
... and so on ...

Is this enough? Will it show me all the bandwidth use of mumble, when I write:

Iptables –L mumble -v

---

