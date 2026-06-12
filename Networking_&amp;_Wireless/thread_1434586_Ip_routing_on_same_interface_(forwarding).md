---
title: "Ip routing on same interface (forwarding)"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by jmazaredo on 2010-03-20
Scenario:

I have a ubuntu box where its ip is from a dhcp server (wireless router)
Inside the box is a virtualbox with windows xp and a webserver. The virtual guest's network is bridged so they are both in same network. 192.168.x.x network.

ip of the virtual guest is 192.168.0.155
ip of the main pc ubuntu is 192.168.0.101

I want to forward the port 80 of the ubuntu (192.168.0.101) to the virtual 192.168.0.155

```
iptables -A PREROUTING -t nat -i wlan0 -p tcp --dport 80 -j DNAT --to 192.168.0.155:80
iptables -A INPUT -p tcp -m state --state NEW --dport 80 -i wlan0 -j ACCEPT
```

is this correct?

---

