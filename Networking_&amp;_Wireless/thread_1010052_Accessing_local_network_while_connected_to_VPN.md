---
title: "Accessing local network while connected to VPN"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by wetling on 2008-12-13
On my Windows machine, I can connect to my work network through the VPN (assigned a 10.x.x.x address) and still access resources on my home network (192.x.x.x).

With VPNC, I can't do that, no local network resources are available. 

What do I need to put into my .conf file so 192.x.x.x traffic is considered local?

Thanks.

---

### Post by wetling on 2008-12-17
I'm now connecting with the Network Manager gui instead of the VPNC cli.  Anyone know how to allow local network access?

---

### Post by joebeasley on 2008-12-18
Using the gui, go to IPv4 Settings, routes.  Manually enter the route for the 10 network (10.0.0.0 255.0.0.0) with no gateway and check the box at the bottom to "ignore automatically obtained routes".  

The remote server is probably sending you a default route.

---

### Post by wetling on 2008-12-18
My config file already had three IP's and their associated subnet masks (no gateway) so all I did was check the "ignore" box but it didn't help.

Any other thoughts?  Thanks.

---

