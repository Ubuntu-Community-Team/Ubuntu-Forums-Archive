---
title: "(ask) Ubuntu Failover Routing ?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by romizone on 2009-02-01
[COLOR="Blue"]
My questions is "Is it works for ubuntu server ?
Anybody have an experience ? create a ubunu server as gateway ?

Obviously i want create my ubuntu box as a router.
the scenario is when the first default gateway down, we loop to another gateway.

Thanks 

Best regard

Romi Nur Ismanto



[/COLOR]


Enabling failover routing

After you have configured your network, the next step is to enable
failover routing on your Linux box, so that if the first route dies the
router will automatically switch over to the next route. To do so,
you'll need to add the default gateway routes provided to you by your
ISPs for both your network cards:

# route add default gw 61.16.130.97 dev eth0

# route add default gw 200.15.110.90 dev eth1

Finally, modify the /proc/sys/net/ipv4/route/gc_timeout file. This file
contains a numerical value that denotes the time in seconds after which
the kernel declares a route to be inactive and automatically switches to
the other route if available. Change its default value of 300 to some
smaller value, say 10 or 15. Save the changes and exit. 

# echo "10" > /proc/sys/net/ipv4/route/gc_timeout

Now your Linux machine is ready to serve as a failover router,
automatically and quickly switching to the secondary route every time
the primary route fails. 
--------

---

### Post by GaganBrahmi on 2009-03-27
Well this looks good for a failover from primary to secondary routing. But my question here is how will kernel determine once the primary route is back and how the switch over will work?

---

