---
title: "Redirecting network traffic (except VPN and DHCP) through VPN"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by stoone on 2008-12-26
I have a working VPN connection (tcp port 19000) through the interface tap0 it's address is 192.168.1.6. I connect to the Internet with wifi through the interface ra0 whom gets it's address via DHCP. I want to redirect all my communication to the VPN when I use insecure wireless APs.

I made a copy of my main routing table and changed the default gateway to my VPN's one with:

```

ip route show table main | grep -Ev ^default | while read ROUTE ; do ip route add table 6 $ROUTE ; done
ip route add table 6 proto static default via 192.168.1.254
```

Then marked all my traffic expect VPN and DHCP traffic with:

```

iptables -t mangle -A OUTPUT -p udp --dport ! 67:68 -j MARK --set-mark 6
iptables -t mangle -A OUTPUT -p tcp --dport ! 19000 -j MARK --set-mark 6
iptables -t mangle -A OUTPUT -p icmp -j MARK --set-mark 6
```

Then I've set up NAT to my interfaces to translate the source address with:

```

iptables -t nat -A POSTROUTING -o tap0 -j SNAT --to-source 192.168.1.6
iptables -t nat -A POSTROUTING -o ra0 -j SNAT --to-source `ifconfig ra0|grep 'inet addr'|cut -d':' -f2| cut -d' ' -f1`
```

And fired up my new routing table to my marked packages:

```

ip rule add fwmark 6 table 6
ip route flush cache
```

I monitored the my tap0 interface. When I try to ping something I can see the request packets go out and the reply packets come in but my ping shows 100% packet loss, this is the same when I try to connect to a TCP server, I can see the SYNs go out and then the SYN-ACKs come in but my program don't gets them.

Where is the problem where my packets got lost?

---

