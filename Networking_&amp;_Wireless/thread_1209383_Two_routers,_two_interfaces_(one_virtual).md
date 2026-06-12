---
title: "Two routers, two interfaces (one virtual)"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by eyko on 2009-07-10
Hi, I'm trying to set up my server with two routers to the Internet but can't seem to get it working, so I come for some help...

My set-up is the following: 


[LIST]
[*]There are two Internet Providers, both in the same network. I'll call them gw1 and gw2. gw1 is 192.168.1.100, and gw2 is 192.168.1.200.
[*]All the computers in the network (including the server) use gw1 (192.168.1.100) for access to the internet at the moment (and should remain that way). The DHCP pool goes from 192.168.1.20-90 for workstations
[*]There is a switch where the whole network is connected to: gw1, gw2, workstations, my home server.
[*]My server has one physical network interface, but I set up two IPs (one virtual interface). So that leaves eth0: 192.168.1.10, and eth0:0 192.168.1.11 (static IPs)
[/LIST]

Okay, so all traffic goes through gw1 (x.x.x.100). The second router, has a static IP and is used for the web server mainly, and then some other less important services. So, from GW2 I have forwarded the http/https, ssh, etc, ports to the server's virtual eth0:0 192.168.1.11. 

Now, what I'm trying to do is to configure the server to use both routers, but only one for each IP, that is, all traffic should go through gw1, except when it's coming from gw2. By default, I want the server to connect using eth0 (192.168.1.10) through gw1 (192.168.1.100), but when traffic comes in through eth0:0 (192.168.1.11), it should go back through there (and through its own gw2).

More or less, it would look like this: 

eth0 => 192.168.1.10 via 192.168.1.100 **(default)**
eth0:0 => 192.168.1.11 via 192.168.1.200

I've tried configuring with ip route following the info from [http://lartc.org/lartc.html#LARTC.IPROUTE2]("http://lartc.org/lartc.html#LARTC.IPROUTE2") (Routing for multiple uplinks/providers), but with no luck, I don't really understand how ip route works... I guess. 

Does anyone know how I could try setting this up?

---

### Post by syadnom on 2009-07-28
A bump here.  I have a very similar need

I want to do this to move my email server between 2 connections and not have to wait for a DNS update.

server has
eth0 WAN interface 71.x.x.x gw is is 71.x.x.1 (old DSL)
eth1 LAN interface 10.223.8.7 gw 10.223.8.3
eth1.1 LAN interface2 10.223.8.220 gw 10.223.8.3
10.223.8.3 is a cisco router on a 10Mb link.

I have a firewall that is taking a public IP and forwarding it to 10.223.8.220 but the default gw on the machine is out the eth0 interface.

I want to make it so that the route used from traffic coming in on eth0 goes out eth0's gw which is the old DSL and traffic coming in on eth1.1 goes out eth1.1's gateway of 10.223.8.3 which is the 10Mb link.

The problem right now is that traffic coming in eth1.1 still goes out eth0 which does not work.

I think that the fix for the OP is the same for me.

I have read a bit on doing 2 different routing tables and applying a routing table for each interface when using 'route add' but need some help actually accomplishing that.

thanks

---

