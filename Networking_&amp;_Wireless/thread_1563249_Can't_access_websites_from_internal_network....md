---
title: "Can't access websites from internal network..."
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by dschuett on 2010-08-28
I am in the process of setting up my own Linux gateway/firewall using two nics eth0(external network) and eth1(internal network). The Linux gateway hands out ip addresses using dhcp3-server, and uses iptables to route the traffic correctly. Clients are able to connect and access the internet...everything is working great, HOWEVER I can't access my apache virtual hosts websites from the internal network? They work just fine if i access them from the outside network...

I can type ip of the web server, 192.168.0.201 and it shows the first virtual host listed in my /sites-enables/000-default folder,but none of my NameServers work. I don't have any internal DNS servers running. This doesn't makes sense, because if i replace the linux firewall/router with my normal linksys wrt54G router it works just fine.

Here is my IPTABLES script:
NOTE: my web server is running on 8080
```

#!/bin/bash

IPT=/sbin/iptables

#flush rules
$IPT -F
$IPT -X
$IPT -F -t nat

#default policies and define chains
$IPT -P OUTPUT ACCEPT
$IPT -P INPUT DROP
$IPT -P FORWARD DROP

#allow established connections
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#accept all connections on lo and Lan
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A INPUT -i eth1 -j ACCEPT

#external access
#$IPT -A INPUT -p tcp --dport 22 -j ACCEPT

#squid
#$IPT -t nat -A POSTROUTING -i eth1 -p tcp -d ! 192.168.0.0/24 --dport 80 -j DNA                                                                             T --to 192.168.0.1:3128

#allow only certain icmp

#0 => echo reply
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT

#3 => Destination Unreachable
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT

#11 => Time Exceeded
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT

#8 => Echo
#avoid ping flood
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT

#port forwards
$IPT -A PREROUTING -t nat -i eth0 -p tcp --dport 2020 -j DNAT --to 192.168.0.201                                                                             :2020
$IPT -A FORWARD -p tcp -d 192.168.0.201 --dport 2020 -j ACCEPT
$IPT -A PREROUTING -t nat -i eth0 -p tcp --dport 8080 -j DNAT --to 192.168.0.201                                                                             :8080
$IPT -A FORWARD -p tcp -d 192.168.0.201 --dport 8080 -j ACCEPT


#masquerade internal address as extenal IP, drop invailid connections, allow unr                                                                             estriced outbout access
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE
$IPT -A FORWARD -i eth1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i eth0 -o eth1 -m state --state NEW,ESTABLISHED,RELATED -j ACCE                                                                             PT
$IPT -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

exit 0

```

---

