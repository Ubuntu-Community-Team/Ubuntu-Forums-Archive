---
title: "iptables - ip rule - fwmark"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by gui076 on 2009-04-07
I changed my distribution for an Xubuntu one and it works great :-)

Hello all,

I try to find help here because it's an active forum :-)

This is my configuration :

[IMG]http://swl76.free.fr/network/network.jpg[/IMG]

I would like to use the Red Internet for HTTP and Green Internet for e-mails.

I searched a lot on google and I saw something with fwmark, ip rule etc... but It doesn't work like I would.

So first I tried with icmp. My problem is with the routing table because when I add :

ip rule add fwmark 10 table 100

ip route add default via GREEN_Network_next_interface table 100

I have all my traffic redirected on the Green_network because of the new route.

I think I missed something :-)

Does anyone have an idea ?

Sorry for my english, I try to improve it ;-)

Thanks

---

### Post by gui076 on 2009-04-07
Hi,

I am trying to experiment with fwmark with my xubuntu distrib but it's very strange.

My config :

Internet<-->192.168.2.0/24<-->Xubuntu<-->192.168.1.0/24<-->Internet

I managed to redirect the icmp request to a specific IP but the problem is that I see the answer on wireshark on the interface but not in the terminal which initiated the ping :-(

**NAT tables** :

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
SNAT       all  --  anywhere             dns3.proxad.net     to:192.168.1.105 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

**MANGLE table** :

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
MARK       icmp --  anywhere             dns3.proxad.net     MARK set 0xa 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination  

**FILTER Table** :

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

**ip rule** :

0:	from all lookup local 
32765:	from all fwmark 0xa lookup 100 
32766:	from all lookup main

details of main :
192.168.2.0/24 dev ath0  proto kernel  scope link  src 192.168.2.254  metric 2 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.105  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.2.1 dev ath0  proto static

details of table 100:

default via 192.168.1.1 dev wlan0


Any idea ?

---

