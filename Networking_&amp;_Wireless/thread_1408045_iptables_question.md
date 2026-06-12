---
title: "iptables question"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2010-02-15
I use ddwrt to redirect traffic to my squid/dansguardian box. It does this transparently using the iptables script below.

#!/bin/sh
PROXY_IP=192.168.1.2
PROXY_PORT=8080
LAN_IP=`nvram get lan_ipaddr`
LAN_NET=$LAN_IP/`nvram get lan_netmask`
iptables -t nat -A PREROUTING -i br0 -s $LAN_NET -d $LAN_NET -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -i br0 -s ! $PROXY_IP -p tcp --dport 80 -j DNAT --to $PROXY_IP:$PROXY_PORT
iptables -t nat -I POSTROUTING -o br0 -s $LAN_NET -d $PROXY_IP -p tcp -j SNAT --to $LAN_IP
iptables -I FORWARD -i br0 -o br0 -s $LAN_NET -d $PROXY_IP -p tcp --dport $PROXY_PORT -j ACCEPT
iptables -t nat -I PREROUTING -i br0 -s 192.168.1.5 -j ACCEPT

the final command allows 192.168.1.5 to bypass the filter. This would be the only device in which apt-get and spybot updates works from. (Nevermind how one device can do both of those things.) I'm not real slick with iptables, but I'm thinking maybe the router box is dropping all non port 80 traffic except for device 192.168.1.5. More than likely apt and spybot use https, so what would be the iptables rule to allow _all_ traffic on port 443 to bypass the filter?

Does apt-get (and spybot updates) use a different port than 443?

---

