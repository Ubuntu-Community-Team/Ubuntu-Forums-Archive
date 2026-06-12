---
title: "ubuntu server 10.10 64 bit... 2 handle two networks"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by schoudhary on 2011-02-09
Hi All,


i have 2 broadband connections 16 mbps and 8 mbps.
16 mbps is connected with LAN and using the switch it is distributed to everybody.
8 mbps is connected to a wifi router and wifi people(iMAC etc) use that.

Now i have a server(ubuntu server 10.10 64 bit) with 4 Ethernet ports and i want to make it as a server to both side of people (wifi and lan) so they can use this computer as a server(e.g. for svn etc), currently both world can't interact with each other bcoz they are on different networks.

I took 2 Ethernet wires one from the LAN switch and put it on the eth0 of the server, another second wite from the wifi router and out on the server's eth1 port.


Here is the network configuration...
#########################
eth0 (16 mbps /LAN)
ip address: 192.168.1.4
Broadcast address: 192.168.1.255
Subnet mask: 255.255.255.0
Default route/gateway: 192.168.1.1
Pri DNS: 1xx.22.xx.xx5	
sec DNS : 1xx.24.xx.xx5

#########################

eth1 (8 mbps/wifi)
ip address:192.168.1.5
Broadcast address: 192.168.1.255
Subnet mask: 255.255.255.0
Default route/gateway: 192.168.1.3
Pri DNS: 1xx.22.xx.xx5
sec DNS : 1xx.24.xx.xx5

#########################

Now we use unique ip for both wifi and LAN connections it start from the 192.168.1.11 till 192.168.1.90


Plaese let me know that how can i setup this by using both broadband connection , both side can use it as a server (e.g. svn server etc) and if possible like running the dhcp server, load balancing of both broadband connection so computers will go through from the server for the Internet.

i have tried bridge & bonding too... :-(

Again thank you for your time and efforts.

-Sandy

---

