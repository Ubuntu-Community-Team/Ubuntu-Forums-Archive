---
title: "I seem to have borked my router"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by woodmaster on 2010-04-04
I have a Belkin Wireless G F5D7230-4.  I was attempting to configure a wireless card on another computer on my network when it froze during the reboot phase after making settings adjustments.  The wired connection is fine, except on that computer that I was making the adjustments from.  It won't connect at all.  I plugged a friends netbook into the same wired line and it connected.  Also there is no wireless signal on any laptops.  Mac, Win Linux, don't matter.  I tried all the various methods of resetting to default but still when I try to access the router's config page @ [http://192.168.2.1](http://192.168.2.1) I get the error ```
The server at 192.168.2.1 is taking too long to respond.  
``````
 $ sudo route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.44.176.0     0.0.0.0         255.255.248.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         70.44.176.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by MooPi on 2010-04-04
Can you still reach the web interface for your router? If so I'd set back to default and then config your wireless card. Don't bork the entire network for one connection.

---

### Post by woodmaster on 2010-04-04
> **MooPi said:**
> Can you still reach the web interface for your router? If so I'd set back to default and then config your wireless card. Don't bork the entire network for one connection.

No.  This is what I get:

>  	Code:
 	The server at 192.168.2.1 is taking too long to respond. 


---

