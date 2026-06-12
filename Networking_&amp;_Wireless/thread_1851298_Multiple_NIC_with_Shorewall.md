---
title: "Multiple NIC with Shorewall"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by marquix on 2011-09-28
I have a Linux box with shorewall installed,
the IP Address is 192.168.1.10 and 192.168.2.10 (Two NICs)

The two NICs connect with two different network, the configuration is shown below:

eth0
IP 192.168.1.10
Netmask 255.255.255.0
Broadcast 192.168.1.255
Gateway 192.168.1.1

eth1
IP 192.168.2.10
Netmask 255.255.255.0
Broadcast 192.168.2.255
Gateway 192.168.2.1

There is a SSHD, and Apache running in the server.
At the same time, both gateway are routers with NAT configured:
in Router #0
Port 22,80 forward to 192.168.1.10
and
in Router #1
Port 22,80 forward to 192.168.2.10

I want both nic listen the Port 22 connection from both WAN.

I have checked to use Shorewall Provider configuration

WAN1	1	1	main	eth0	192.168.1.1	       track,balance	
WAN2	2	2	main	eth1	192.168.2.1 	track,balance=2	


the ip route list result is:

192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.10 
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.10 
default 
	nexthop via 192.168.1.1  dev eth0 weight 1
	nexthop via 192.168.2.1  dev eth1 weight 2




I have the problem that:

when i use wget -c [address here]

--2011-09-28 13:16:08--  ht tp://www.google.com.hk
Resolving [address here]... 74.125.71.105, 74.125.71.106, 74.125.71.147, ...
Connecting to [address here]... connected.
HT TP request sent, awaiting response...

It connected but no response for a long time... ...

Can anyone here can answer my questions?
When i connect the SSHD from EXTERNAL network, I got no problem !!!

---

