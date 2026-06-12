---
title: "Slow DNS lookup 8.04.3 (iptables related)"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by downhillgames on 2009-11-18
Hello there, folks. First and foremost, I'm just getting my feet wet with "D.I.Y. networking" if you will. *Surely* I'm just overlooking something obvious.

I have an Ubuntu Server 8.04.3 router/MASQUERADE/firewall/DNS/DHCP box here that is having trouble with DNS queries, but *only when I mess with iptables as described below.*

Since this is a test box, iptables is empty besides MASQUERADE'ing a subnet out eth0. The first thing I'd like to do is drop all incoming connection requests from the external network (eth0), however I want to allow **all** traffic from my box (also joined on the private subnet for testing purposes) so as to avoid accidentally DoS'ing myself from the router. For this I have made the following iptables rule:
```
iptables -A INPUT -t filter -s 192.168.1.50 -d 192.168.1.1 -j ACCEPT
```
This is where the trouble starts. When I change the default policy to DROP (iptables -P INPUT -t filter DROP), DNS goes *dog* slow. It's just unbearable. `iptables -L` takes a long time, but `iptables -n -L` is instant. Same with `route` and `route -n`, etc.

What did I miss?

PS: /etc/host.conf has "order hosts,bind" but /etc/hosts is empty except localhost, so I know it's not my /etc/hosts file. 

PPS: DHCP hands down 192.168.1.1 for the DNS server to all the (DHCP) clients on 192.168.1.0/24, they get correct addresses and everything works until I change iptables. Like I said, looks like I'm overlooking something simple, but I don't know what it is because I'm still wrapping my head around a lot of information :) Any help would be greatly appreciated.

---

### Post by downhillgames on 2009-11-19
So I got DNS working with the subnet while INPUT from the filter table is set to DROP by default with the following iptables rule:
```
iptables -A INPUT -t filter -i eth0 -p udp --sport 53 --dport 53
```

While this works in a controlled environment, I don't think this is optimal being as my Internet address is assigned by DHCP from my ISP. That said, I don't know how to make this forward any other way. Is it considered "good practice" to forward to/from an interface (NIC) like that?

---

