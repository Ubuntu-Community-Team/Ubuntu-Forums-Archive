---
title: "Routing for 2 NICs, to split traffic between NAS and everything else"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by thedaver on 2010-06-13
I have a Ubuntu/Mythbuntu (backend) server.  I also have a network attached NAS device that exposes shares/ftp/NFS mount points.

I've installed a second NIC in the server and I'd like to segment/separate the traffic on the server so that all traffic to the NAS uses one specific card and all other traffic to users, Internet, etc. goes on the other card.

Presently my home network is 192.168.1.0/24.  Server's first NIC is 192.168.1.20.  NAS is 192.168.1.66.  All running through one HP switch, so I don't really have switching options.

I had considered a couple of options.  

Introduce another netblock 192.168.2.0/24, re-IP the NAS onto that netblock and force a route in the server for that netblock.

Other option was to somehow leave the NAS in the 192.168.1.0/24 netblock but put a routing rule on the server so that the NAS' IP had to go out the second NIC.

I'm fairly sure I can put together a routing rule for the first case, but I have no idea how to route the second option (one IP through second NIC in the same netblock).

I've got all the flexibility in the world to mess around with my addressing on my home network.
TIA

---

### Post by thedaver on 2010-06-14
Server has two NICs in subnet 192.168.1.0/24
first NIC: 192.168.1.20/32
second NIC: 192.168.1.21/32
NAS IP is 192.168.1.66/32

I want server's routing for requests to NAS to go thru second NIC.  Extra points if routing priority fails back to the first NIC if the second NIC fails (not congested, but fails)

All other traffic goes thru first NIC.

How to set this up with "route" commands is needed.  I've got it to here, but it's not working correctly.

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.66    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by Iowan on 2010-06-14
Threads merged.

Someday, I'll find a link to the documentation that it's a violation of protocol to have two IP's in the same subnet. Sounds logical - since it plays havoc with routing, but I don't have it available - so I can't claim it's true. You "might" be able to set up iptables rules...

---

### Post by thedaver on 2010-06-14
Well, I can't speak to a violation of protocol, but it's fairly common to isolate traffic to NICs for backup, NAS, etc...  Yeah, those tend to be on different subnets and switches, so this homebrew hobby thing is sort of a fit-for-purpose request.

I think I actually have it working...

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.66    192.168.1.21    255.255.255.255 UGH   0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


This allows for a route the seems to only allow 192.168.1.66 via eth1, everything else passes over eth0.  It would be uber cool to get a lower priority path for .66 over eth0.  But for now, the goal is mostly met.

---

### Post by capscrew on 2010-06-14
> **thedaver said:**
> I have a Ubuntu/Mythbuntu (backend) server.  I also have a network attached NAS device that exposes shares/ftp/NFS mount points.

I've installed a second NIC in the server and I'd like to segment/separate the traffic on the server so that all traffic to the NAS uses one specific card and all other traffic to users, Internet, etc. goes on the other card.

Presently my home network is 192.168.1.0/24.  Server's first NIC is 192.168.1.20.  NAS is 192.168.1.66.  All running through one HP switch, so I don't really have switching options.

Is there some particular reason that you want to dedicate a separate NIC to the NAS device?  The NAS is a separate endpoint on the 192.168.1.0/24 network.  The *server* and the NAS are peers in the network.  A network card is only a device to provide connectivity between the two hosts.  
> 


I had considered a couple of options.  

Introduce another netblock 192.168.2.0/24, re-IP the NAS onto that netblock and force a route in the server for that netblock.

Other option was to somehow leave the NAS in the 192.168.1.0/24 netblock but put a routing rule on the server so that the NAS' IP had to go out the second NIC.

I'm fairly sure I can put together a routing rule for the first case, but I have no idea how to route the second option (one IP through second NIC in the same netblock).

I've got all the flexibility in the world to mess around with my addressing on my home network.
TIA

The only possible method to is to place the NAS on a separate subnet (i.e. 192.168.2.0/24 or some such) and add routing services to you server.

I'm sure you are wondering why you can't you just add another NIC to the same subnet as the first NIC?  The simple answer is that there is a protocol used with Ethernet that prevents you.  It is known as Spanning Tree Protocol (STP).  It disables those links that are not part of the spanning tree (I.e. parallel layer 2 connections), [COLOR="Red"]**leaving a single active path between any two network nodes**[/COLOR] (1)

Another way to look at this is: "By definition of the Ethernet network topology, [COLOR="Red"]**only one adapter may communicate on the [COLOR="Black"][local][/COLOR] network at the same time**[/COLOR]. Therefore, both adapters cannot be transmitting at the same time and must wait if another device on the network is transmitting." (2)

See [**_here _**]("http://en.wikipedia.org/wiki/Spanning_tree_protocol")(1) and [**_here_**]("http://support.microsoft.com/default.aspx?scid=kb;EN-US;175767") (2).

---

### Post by bsgcic on 2010-07-27
[]("http://ubuntuforums.org/member.php?u=911491")thedaver - what were the commands that you used to achieve the results of route -n that you posted?
I am trying to do something similar:
[http://ubuntuforums.org/showthread.php?p=9633579#post9633579](http://ubuntuforums.org/showthread.php?p=9633579#post9633579)

Thank you

---

