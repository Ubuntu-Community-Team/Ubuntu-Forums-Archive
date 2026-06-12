---
title: "Routing between subnets in testenvironment fails randomly"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by volzon on 2010-02-03
Hi.
 
I've a test environment to test workstations and servers before I install them in to our network.
 
I'm using at Ubuntu Live CD and a script to set up all our gateways and route between them. The problem is that the routing between the networks comes and goes.
 
It seems the routing is working, but randomly fails for one of the subnets at a time.
 
Here is my script:
```
 
#!/bin/bash
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -X
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth0 -j ACCEPT
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
 
#Defining gateways for the subnets
sudo ifconfig eth0 10.200.60.1 netmask 255.255.255.0
sudo ifconfig eth0:0 10.200.26.1 netmask 255.255.255.0
sudo ifconfig eth0:1 10.245.33.1 netmask 255.255.255.0
and so on... 20 subnets

```
 
I've tried with reducing the number of subnets, but the problem continues

---

