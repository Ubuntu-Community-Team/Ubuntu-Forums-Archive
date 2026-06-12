---
title: "openvpn iptables protection"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by jamrop on 2013-01-30
Hey

I have ubuntu as a vpn gateway for my local network

My openvpn uses tap interface

I am worried that if i lose my openvpn connection, my local network (eth0) will be wild open 

I was wondering if i am missing something in iptables to secure it more, for example if i lose my openvpn, to stop my local network accessing the internet, or if there is something else i can do? reconnect?

Also, is there anything else not in my iptables to make it more secure from attacks hacks etc?

It gets a bit confusing with Forwards and Output for me lol. Still trying to learn it.

Many many thanks

Below is my iptables list

FORWARDS
```
iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o tap0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i tap0 -p tcp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD -i tap0 -p udp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD -i tap0 -p tcp -m tcp --sport 80 -j ACCEPT 
iptables -A FORWARD -i tap0 -p tcp -m tcp --sport 443 -j ACCEPT 
iptables -I FORWARD -p tcp --dport 1194 -j ACCEPT
iptables -I FORWARD -p udp --dport 1194 -j ACCEPT
iptables -A FORWARD  -p tcp -m tcp --sport 6667 -j ACCEPT 
iptables -A FORWARD  -p tcp -m tcp --sport 6697 -j ACCEPT 
iptables -A FORWARD  -p tcp -m tcp --sport 9050 -j ACCEPT
iptables -A FORWARD  -p tcp -m tcp --dport 9050 -j ACCEPT
iptables -A FORWARD -i tap0 -j DROP
```


OUTPUTS
```
iptables -A OUTPUT  -p tcp -m tcp --dport 6667 -j ACCEPT 
iptables -A OUTPUT -o tap0 -p udp -m tcp --dport 133 -j ACCEPT 
iptables -A OUTPUT -o tap0 -p tcp -m tcp --dport 80  -j ACCEPT
iptables -A OUTPUT -o tap0 -p tcp --sport 0:65535 --dport 53 -j ACCEPT
iptables -A OUTPUT -o tap0 -p udp --sport 0:65535 --dport 53 -j ACCEPT
iptables -A OUTPUT -p icmp -o tap0 -j DROP
iptables -A OUTPUT -o tap0 -j DROP
```

INPUTS
```
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -d 127.0.0.0/8 ! -i lo -j REJECT --reject-with icmp-port-unreachable
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -j ACCEPT
iptables -A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
iptables -A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
iptables -A INPUT -i eth0 -p tcp  --dport 22 -j ACCEPT
iptables -A INPUT -j REJECT --reject-with icmp-port-unreachable
iptables -A INPUT -i tap0 -j DROP
```

---

