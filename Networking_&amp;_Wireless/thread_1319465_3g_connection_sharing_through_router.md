---
title: "3g connection sharing through router"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by masque7 on 2009-11-08
When I am connected via my modem if I connect wirelessly to my router or via ethernet, I get no connection. I am having trouble understanding why. It seems unable to receive DHCP when I do this (cannot get IP from router).

Is it possible to share the mobile broadband connection from a 3g USB modem via my router? I know this is possible on Windows XP - networking -> modem -> "share this connection". Also, being connected wired or wirelessly doesn't drop the connection/block DHCP. 

I've googled,  but it was very complex. I found [this]("http://linfiniti.com/2009/06/sharing-a-3g-modem-connection-with-ubuntu-jaunty/")

I now know it *is possible* but I am looking for an explanation why this is problematic. What's Windows doing that Ubuntu isn't? If anyone can explain in simpler terms the procedure I would take to set this up, we could merge this with a lot of blank threads for this query.

```
modem: Huawei E220
router: Linksys wrtg54 - tomato firmware
Ubuntu 9.04
```Thanks in advanced

---

### Post by leosaguiar on 2010-04-24
Hi,
 
I am having the same problem. While my router is on-going, i cant connect on my USB MODEM. I receive a " cant find modem" message on Gnome PPP.  
 
Another information that can be interesting is that for my router be seen on my Ubuntu Box , i had to edit /etc/network/interfaces with the router´s Ip (192.168.0.1)
 
Did you resolve your issue? How was that?
 
Thanks

---

