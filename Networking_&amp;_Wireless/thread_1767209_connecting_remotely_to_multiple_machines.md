---
title: "connecting remotely to multiple machines"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by bigmonmulgrew on 2011-05-25
Not sure if this should go in the server section but here goes

I currently have a virtual webserver running on my desktop PC.
My router is set to forward http,ssh etc ports to the ip address of this vpc. This works fine as is. I can connect via ssh to the server both locally and from another site.

I'm now trying to setup a Host server and a new virtual server on that, with a few other VPCs as well

I can ssh to the new host server and the new virtual server using their local IP addresses. Obviously I can still only access the same vPC externally.

I want to be able to access both the new host server, new virtual server and any other virtual servers I may create in the future. The old VPC running on my desktop will be removed when the new one is setup.
How do I configure it so I can access any/all of my PC/vPCs externally.

My router is a netgear DGN2000
This is also currently my DHCP server

My existing host PC is a windows 7 Pc running Virtual box
The existing virtual guest is ubuntu 10.10 server setup as a LAMP

The new host is ubuntu 11.04 server
The new guest is ubuntu 11.04 server 

If someone could point me in the right direction to get started I would be very greatful.

---

