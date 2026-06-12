---
title: "Ubuntu  will not allow other subness access"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by catsrules on 2012-01-01
I can't access my Ubuntu web server from another subnet, and it looks like it is being blocked by ubuntu it self I have check the routers and stuff and they are all working, it is just this 1 that isn't. This server has two nic running two different web servers on each. I can access one of the nic (eth0) but not the other one (eth1). I also can ping the work nic (eth0) but not eth1. eth1 was added later after Ubuntu was installed, if that make any difference.
Both nics work fine if I am on the same subnet as they are.

Does Ubuntu have a firewall or something that is blocking access for the other subnets? 

thanks

---

### Post by Iowan on 2012-01-02
**eth1** has an IP address? Check/post **ifconfig -a**

---

### Post by catsrules on 2012-01-03
Yes eth1 has an ip address
Network configuration

eth0 and eth1 is on 172.16.10.0 /24 subnet 

eth0 
IP=172.16.10.11
Sub 255.255.255.0

eth1
IP=172.16.10.12
Sub=255.255.255.0

The other subnet is for VPN clients on 172.16.1.0 /24
This subnet can not access the server on the eth1 nic, but it can on the eth0 nic.
But clients on the 172.16.10.0 /24 subnet can access both nic with out a problem.

---

### Post by catsrules on 2012-01-04
I got it working, got some downtime and rebooted the server, and that fixed it.

Thanks for you help

---

