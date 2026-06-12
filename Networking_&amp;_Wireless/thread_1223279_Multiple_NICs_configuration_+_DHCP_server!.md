---
title: "Multiple NICs configuration + DHCP server!"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by futuregenious on 2009-07-26
Hey all,

I am working in a country on a project for helping a school and do not have great internet connectivity. So would be really glad if you could help me with this!

I am running Ubuntu JJ 9.04 as a server in the school network. Its currently running Apache, BIND, PROFTPD, and a DHCP server.

Both the NICs are connected to a switch which is connected to a router. The router connects to the Internet and to the entire school network. I want the server to function as a DHCP server (after disabling it on the router). 

Although I was able to run it (server) as a DHCP server, I failed to succeed completely. I want the traffic to pass through one NIC, which I assume would be a gateway and the one which runs the DHCP server. And consequently, the response back goes from the other NIC.

I read a few articles on the Internet which required me to set up routing. The good thing is that Ubuntu has great GUI tools for setting this up. But I am unable to do it! Please could you guide me.

Info:

Linksys Router IP: 192.168.3.3 (Connected to DSL connection)
eth0 Static IP: 192.168.3.100 (running DHCP server)
eth1 Static IP: 192.168.3.101 (the second NIC on the machine)
Subnet for all: 255.255.255.0

Any help is really appreciated. Thanks!

Varun

(Is there an easier way to set a network host which would allow users on the network to access a node without its ipv4 address? The only obvious solution for me seems to set it on the DHCP server as fixed host. I don't want to go into the hassle of setting up a DNS)

---

### Post by superprash2003 on 2009-07-26
both NICS are connected to the switch? wouldnt it be better , if one NIC is connected directly to the router ( no other machine to be connected to router ) and the other NIC to be connected to the switch which inturn is connected to all machines..
  then configure DHCP server and internet connection sharing 
1)[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
2)[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by Iowan on 2009-07-26
I moved my DHCP server from the router to a separate server... but that server has only one NIC.  It points to router as gateway and DNS server.

---

