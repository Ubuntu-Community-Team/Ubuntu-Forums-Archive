---
title: "Trying to NAT with Iptables, traffic can't get out"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by VMOS on 2013-08-17
Hello, I'm building a little mail platform and I've got ubuntu 13 with haproxy in front of a few postfix servers and that. Based on the instructions here [http://blog.loadbalancer.org/configure-haproxy-with-tproxy-kernel-for-full-transparent-proxy/](http://blog.loadbalancer.org/configure-haproxy-with-tproxy-kernel-for-full-transparent-proxy/) I configured haproxy to use transparent mode so the clients Ip shows up in the backend mail servers, that all works perfectly fine.
Now I need to get those backend servers (which are now using the haproxy box as their gateway) to be able to access the intertubes themselves. I've found a bunch of slightly different methods for this, but so far none of them work. Here's what I've got in /etc/rc.local, I've tried all of those rules that are currently hashed out

```
iptables -t mangle -N DIVERT
iptables -t mangle -A PREROUTING -p tcp -m socket -j DIVERT
iptables -t mangle -A DIVERT -j MARK --set-mark 111
iptables -t mangle -A DIVERT -j ACCEPT
ip rule add fwmark 111 lookup 100
ip route add local 0.0.0.0/0 dev lo table 100
ip rule add dev eth0 fwmark 111 lookup 100
ip rule add dev eth1 fwmark 111 lookup 100
#iptables -t nat -A POSTROUTING -s 172.1.1.0/255.255.255.0 -j MASQUERADE
#iptables -t nat -A POSTROUTING -s eth1 -j MASQUERADE
#iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -t nat -A POSTROUTING -s 172.1.1.0/255.255.255.0 -o eth0 -j MASQUERADE
#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```

Can anyone give me any pointers as to where I'm going wrong?

/edit, got it this is the config that now works

```
iptables -t mangle -N DIVERT
iptables -t mangle -A PREROUTING -p tcp -m socket -j DIVERT
iptables -t mangle -A DIVERT -j MARK --set-mark 111
iptables -t mangle -A DIVERT -j ACCEPT
ip rule add fwmark 111 lookup 100
ip route add local 0.0.0.0/0 dev lo table 100

iptables -t nat -A POSTROUTING -s 172.1.1.0/255.255.255.0 -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

```

and I needed to edit /etc/sysctl.conf and uncomment this line

net.ipv4.ip_forward=1

bingo, I get traffic forwarded in via haproxy with the source IP showing up at the backend and the backend servers can get out to the intertubes for stuff and things

---

