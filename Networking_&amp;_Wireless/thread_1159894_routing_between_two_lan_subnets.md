---
title: "routing between two lan subnets"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by m0th on 2009-05-15
Hi,
i'm stuck with following situation:
i'm trying to setup linux router to connect two internal subnets.
My current configuration is:
ubuntu server 8.04 lts with two NIC's installed.
NIC1: ip: 10.0.0.101/24 gateway 10.0.0.1
NIC2: ip: 192.168.0.1/24 gateway 192.168.0.1
 
ip_forward = 1
default static routes
The problem is that i can ping and connect to computers in 192.168.0.0/24 network from 10.0.0.0/24 network but can't see the 10.0.0.0/24 network from machines in 192.168.0.0/24 network.
By the way, i don't want to use iptables, becouse i think there must be a solution with static routes or something.
 
please help...

---

