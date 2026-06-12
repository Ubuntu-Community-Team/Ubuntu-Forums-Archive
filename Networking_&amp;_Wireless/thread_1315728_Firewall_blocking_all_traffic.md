---
title: "Firewall blocking all traffic"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by fusa on 2009-11-05
After upgrading to Karmic, my firewall blocks all traffic, including local net, localhost and even accessing web sites.  If I turn the firewall off, everything works normally. One simple script I am trying now is:

```

#!/bin/bash
iptables -F
iptables -X
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
iptables -A LOG_DROP -j DROP
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FIREWALL -i lo -j ACCEPT
iptables -A FIREWALL -o lo -j ACCEPT
iptables -A FIREWALL -j TRUSTED
iptables -A FIREWALL -j DROP
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j DROP
iptables -A OUTPUT -j FIREWALL
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 22 -i eth0 -s 192.168.1.1/24 -j ACCEPT
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 53 -i eth0 -s 192.168.1.1/24 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 53 -i eth0 -s 192.168.1.1/24 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

```

192.168.1.1-255 are the ips my local net use.  eth0 is the network device used to connect to my router, and lo is my localhost.  Does anyone see a mistake in this?  Or something else that could be wrong?  I have had to disable all apparmor profiles since they block several applications from running (aa-logprof no longer works)

---

