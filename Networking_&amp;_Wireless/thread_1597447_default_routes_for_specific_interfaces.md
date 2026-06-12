---
title: "default routes for specific interfaces?"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by wkearney99 on 2010-10-15
I've got a 10.04 machine with two ethernet interfaces.  I have two separate outside internet connections.  This machine is connected to both interfaces.  But it DOES NOT route between them.  It's just a host on both subnets.  Again, no routing is to go through this host. 

I'd like to force traffic originating on each ethernet port out to that network's internet connection. 

Here's the desired setup:
eth0 192.168.12.37/24 gw 192.168.12.1
eth1 192.168.1.37/24   gw 192.168.1.1

I'd like traffic on the 192.168.1.37 address to go out through the 192.168.1.1 gateway. I have a program bound to that address and need it's traffic to go out ONLY through the 192.168.1.1 gateway.  

Any other traffic on the machine should go out the 192.168.12.1 gateway. 

The logic is:
  source IP is 192.168.1.37, dest IP is any then go out only through 192.168.1.1
  source IP is 192.168.12.37, dest IP is any then go out through 192.168.12.1 first or 192.168.1.1 next.

The point is source on the .1.37 address must always go out the .1.1 gateway and NEVER through .12.1.  Whereas traffic on the .12.37 address should try going out the .12.1 gateway first but can go out the .1.1 gateway if the .12.1 connection is down.  I could live with this failover option.  I could accept that traffic on the .12.37 address was likewise limited to its own gateway.

What are the correct routes to set up here?

---

### Post by SeijiSensei on 2010-10-15
This seems to be the question of the day this morning!

See: [http://ubuntuforums.org/showpost.php?p=9976398&postcount=6](http://ubuntuforums.org/showpost.php?p=9976398&postcount=6)

---

### Post by wkearney99 on 2010-10-15
> **SeijiSensei said:**
> This seems to be the question of the day this morning!

See: [http://ubuntuforums.org/showpost.php?p=9976398&postcount=6](http://ubuntuforums.org/showpost.php?p=9976398&postcount=6)

That doesn't quite deal with the question.  This is not a gateway machine.  Traffic does not go through this host.  It has a program running on it that has to be limited in how its traffic is routed. 

The linked post only deals with setting up one default route.  I need two default routes.  I need one for the .1.37 address (the .1.0/24 subnet) and a separate one for the .12.37 address (on the 12.0/24 subnet).  

I realize many users will not need this sort of setup.  This is not a router between the networks.  That's handled by an actual router, not this machine.

---

### Post by SeijiSensei on 2010-10-15
You need "source routing" then.  Read this: [http://lartc.org/howto/](http://lartc.org/howto/)

---

