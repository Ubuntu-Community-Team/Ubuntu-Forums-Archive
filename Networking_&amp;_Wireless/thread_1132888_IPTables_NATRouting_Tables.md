---
title: "IPTables NAT/Routing Tables"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by robTard on 2009-04-22
Here is my setup:

I have two NICS on my box.  

eth0 has IP address: A.B.C.D/24
eth1 has IP address: A.B.C.E/24

I also have coded up a 'tun' device: 
tun0: 192.168.1.1

eth0 'talks' to the internal network, while eth1 talks to the
outside world.  I also have a NAT running on tun0:

iptables -A FORWARD -i tun0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT
iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE

tun0 essentially sits there and captures packets from eth0 and eth1, adds a UDP/IP header (if coming from the outside world and going to my internal network) or strips off a UDP/IP header (if coming from my internal network and going to the outside world) and sends them to my internal network.

I am having trouble setting up the proper routes for this setup to close the loop.

What are the proper routes I need in order for something like this to work?


Here is my iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination        

Chain FORWARD (policy DROP)
target     prot opt source               destination        
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere           
LOG        all  --  anywhere             anywhere            LOG level warning prefix `** WIROVER ** '

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

Here are my current (incorrect) routes:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
174-157-171-52. 128.105.22.226  255.255.255.255 UGH   0      0        0 eth0
128.105.22.99   *               255.255.255.255 UH    0      0        0 eth1
128.105.22.226  *               255.255.255.255 UH    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 tun0
128.105.22.0    *               255.255.255.0   U     0      0        0 eth1
128.105.22.0    *               255.255.255.0   U     0      0        0 eth0
default         128.105.22.99   0.0.0.0         UG    0      0        0 eth1
default         svi-22.cisco1.c 0.0.0.0         UG    0      0        0 eth0

---

