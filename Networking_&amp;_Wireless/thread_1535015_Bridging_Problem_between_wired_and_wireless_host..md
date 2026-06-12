---
title: "Bridging Problem between wired and wireless host."
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by kwikksilva on 2010-07-20
Hi Guys,

In [another thread]("http://ubuntuforums.org/showthread.php?t=1533969"), Marshmallow helped me to setup ICS between

Wireless ETH0 on Server A -> ETH1 Wired on Server A -> ETH0 Wired on Server B

Server A Wireless ETH0  has an ip of 192.168.1.12 from my FIOS router
Server A ETH1 Wired has an ip address of 10.42.43.1
Server B ETH0 Wired has an ip address of 10.42.43.11 (from Server A?)

Problem : Server B can now ping other servers in the network, but no-one can ping Server B at 10.42.43.11

I am not sure how to setup the routing to allow Server B to appear on the network to other servers and clients?

Any ideas? Thanks for your help!

---

### Post by kwikksilva on 2010-07-23
Bumpel-stilts-kin!

---

### Post by kwikksilva on 2010-07-26
Still can't get this working! Bump.

---

### Post by Iowan on 2010-07-26
I haven't been having much luck helping lately, but...
On Server A:
What is in routing table (**route -n**)?
What are results of **iptables -L**?

---

### Post by kwikksilva on 2010-07-26
Hi Iowan,

Thanks a mill for replying

For Server A, here is the output of **route -n**

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```and [B]iptables -L

[/B]```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```Hopefully this helps you - to help me!

---

### Post by Iowan on 2010-07-27
I'm curious (and somewhat confused) that the routing table uses eth0 and wlan0 instead of eth0 and eth1. Is that right?

Understanding **iptables** is still on my "TO-DO" list, but I'm also wondering if the "state RELATED,ESTABLISHED" might be responsible. From [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page:> ... rule2 allows forwarding of established connection packets (and those related to ones that started)


---

