---
title: "can't ssh from external net"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by davidmenges on 2013-01-12
With a new install of 12.04, I cannot ssh (or connect to any port) from an external network:

[FONT="Courier New"]            
from local net to Mac = works
from local net to Ubuntu = works
from external net to Mac = works
from external net to Ubuntu = Connection timed out
[/FONT]

Because of the above testing, and with swapping in/out equipment, I'm convinced it's not a port mapping problem, etc.  I've tested from [http://canyouseeme.org](http://canyouseeme.org) too, with identical results.

Hints, anyone?

---

### Post by ahallubuntu on 2013-01-12
What ports are you forwarding?  What port is the Ubuntu ssh server listening on?  You can't use port 22  externally for both machines - you can only forward one port to one IP, unless the router has some sort of port triggering to switch them on the fly.  Otherwise, you'll have to use some other unused port and forward that to the second machine.

Some routers can forward a source port to a different destination port.  If so, you can keep the Ubuntu ssh server listening on port 22 but have the router forward some other port to port 22 on that IP.  If your router can't forward a port to a different destination port number, you'll have to change what port the ssh server listens on to the same port.

---

### Post by davidmenges on 2013-01-12
The ports I want to forward are 4280 and 4282 (CrashPlan); I just described the problem using ssh as a simple example.  Ubuntu is listening correctly on 22 and on those ports.  I reconfigure the router between tests:  forward 22 to my Mac, test successfully, forward 22 to my Ubuntu box, test unsuccessfully.  I don't need for source/destination ports to be different.

---

### Post by markbl on 2013-01-12
Could be a routing problem. Can you ping the internet from your Ubuntu server?

---

### Post by davidmenges on 2013-01-13
You're right, it was routing.  My net used to be 10.0.x.x but is now 192.168.0.x, and some remnants were left behind.  Once I cleaned everything up, it started working.  Thanks!

---

