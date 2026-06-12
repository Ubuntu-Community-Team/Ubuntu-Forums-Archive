---
title: "Policy Based Routing... help please..."
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by madzieph on 2010-12-24
**Merry Christmas to everyone!!!**

I am trying to setup a multihomed torrent box using policy-based routing on a system running Debian Sid. I suppose that if there is a solution, it would be generally the same for both Ubuntu and Debian. 

If this is not allowed... my apologies.

Network settings are as follows:

**etc/iproute2/rt_tables**
> #
# reserved values
#
255    local
254    main
253    default
0    unspec
#
# local
#
#1    inr.ruhep
100    DSL
125    BRO1
150    BRO2


**/etc/network/interfaces**
> auto lo
iface lo inet loopback

allow-hotplug eth0
allow-hotplug eth1
allow-hotplug eth2
allow-hotplug eth3

# LAN Interface
auto eth0
iface eth0 inet static
    address 192.168.1.50
    netmask 255.255.255.0
    broadcast 192.168.1.255
    post-up ip route add 192.168.1.0/24 dev eth0 src 192.168.1.50 table DSL
    post-up ip route add default via 192.168.1.1 table DSL
    post-up ip rule add from 192.168.1.50 table DSL
    post-up ip rule add fwmark 0x20 table DSL
    post-down ip rule del from 192.168.1.50 table DSL

# WAN Interface &#8211; BRO1
auto eth1
iface eth1 inet static
    hwaddress ether
    address 192.168.248.239
    netmask 255.255.224.0
    network 192.168.224.0
    post-up ip route add 192.168.224.0/19 dev eth1 src 192.168.248.239 table BRO1
    post-up ip route add default via 192.224.1 table BRO1
    post-up ip rule add from 192.168.248.239 table BRO1
    post-up ip rule add fwmark 0x21 table BRO1
    post-down ip rule del from 192.168.248.239 table BRO1

# WAN Interface &#8211; BRO2
auto eth2
iface eth2 inet static
    hwaddress ether
    address 192.168.252.246
    netmask 255.255.224.0
    network 192.168.224.0
    post-up ip route add 192.168.224.0/19 dev eth2 src 192.168.252.246 table BRO2
    post-up ip route add default via 192.168.224.1 table BRO2
    post-up ip rule add from 192.168.252.246 table BRO2
    post-up ip rule add from fwmark 0x22 table BRO2
    post-down ip rule del from 192.168.252.246 table BRO2

# Admin Interface 
auto eth3
iface eth3 inet static
    address 192.168.1.51
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255


**/etc/network/if-up.d/def-route**
> #! /bin/bash
ip route add default scope global nexthop via 192.168.1.1 dev eth0 weight 1 nexthop via 192.168.224.1 dev eth1 weight 1 nexthop via 192.168.224.1 dev eth2 weight 1


**etc/blockcontrol/blockcontrol.conf**
> INIT="1"
WHITE_TCP_IN="ssh 22"
WHITE_TCP_OUT="http https"
WHITE_TCP_FORWARD="51413"
WHITE_UDP_FORWARD="51413"
WHITE_IP_IN="192.168.1.0/24 192.168.2.0/24 192.168.240.0/19 "
WHITE_IP_OUT="192.168.1.0/24 192.168.2.0/24 192.168.224.0/19 "



**Present Scenario:**
1.	If route is set to the one above browsing and torrent won&#8217;t connect.
2.	If route is to a single connection, there is browsing and torrent.
3.	Connections to BRO1 and BRO2 are supposed to get their ip via DHCP but since I need a static ip for setting the routes, I made use of the ip given by DHCP and set them as static. After all, the DHCP server gives 7 days for timeout. 

**Goal:**
1.	Be able to make use of the three (3) connections for bit torrent and other multi-thread programs.
2.	Create a script that can get the ip given by the DHCP server, enter such to the proper interface and create the routing table. (If this is possible in the policy-based routing environment&#8230; just in case the DHCP server is reset and gives out new ip addresses.)

**Some ideas already thought about:**
1.	A multi-wan router would be an easy solution but I can&#8217;t afford it.
2.	Setting up another box running pfSense or any linux router distro but that would just be additional electrical consumption and seems unnecessary in a home setup with just 3 PCs.

By the way, I was able to make this work initially with the BRO connection double-NATed to a router&#8230; but having 3 routers for 3 connections to 1 pc would seem to be superfluous.  

Now, I wonder why the present setup won&#8217;t. 

Anyone care to help?

Thanks.

---

### Post by madzieph on 2011-01-05
solved

---

