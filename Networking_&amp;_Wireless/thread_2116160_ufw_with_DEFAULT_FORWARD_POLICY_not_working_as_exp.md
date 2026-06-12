---
title: "ufw with DEFAULT_FORWARD_POLICY not working as expected"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by illafam on 2013-02-15
I'm trying to setup a firewall.
 
Ubuntu Server 12.04
 
eth0 - external network (192.168.1.0)
eth1 - internal network(10.0.0./24) with an ip of 10.0.0.8
 
All the clients have their gateway set to 10.0.0.8. I want to block everything from all clients by default. There is a few machines that need to make outside connections which I will configure one by one.
 
In /etc/default/ufw I can set the following DEFAULT_FORWARD_POLICY="ACCEPT"
 
If I set this to ACCEPT, all the clients on 10.0.0.0/24 can access the internet. Adding "deny out" using ufw does not stop this from happening.
 
If I set DEFAULT_FORWARD_POLICY="DROP" then none of the machines can access the internet, this is what I want. The problem is if I add an allow out rule, it doesn't seem to work.
 
So for instance: sudo ufw allow out from any to any to port 80
 
Does not allow me to browse the web.
 
I'm not sure how to make this work..

---

