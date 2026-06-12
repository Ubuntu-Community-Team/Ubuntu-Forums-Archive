---
title: "iptables length rule not working"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by hlstriker on 2012-12-30
Hi, I'm trying to use iptables to drop packets that are not between the length of 33-2800.

> iptables -A INPUT -i eth0 -p udp --dport 26900:27050 -m length ! --length 33:2800 -j LOG --log-prefix "SRCDS-BADSIZE " --log-ip-options -m limit --limit 1/m --limit-burst 1
iptables -A INPUT -i eth0 -p udp --dport 26900:27050 -m length ! --length 33:2800 -j DROP

That rule does not seem to be working and I'm not sure why. I sometimes see a packet logged from the rule but it doesn't seem to log/drop all the time.

I was under a DoS attack earlier today with packets of lengths 6-19 so that rule should have logged and dropped those packets right? Needless to say the packets got through to my process and I had to end up making a rule to drop the attackers IP instead.

---

