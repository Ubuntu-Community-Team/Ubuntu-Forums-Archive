---
title: "How to find the subnet of my router?"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by unckybob on 2012-04-04
Can someone tell me how to find the subnet of my router?

---

### Post by sammiev on 2012-04-04
Have you tried this yet?

[PHP]route -n[/PHP]

---

### Post by unckybob on 2012-04-04
Thank you for the quick response. 

If it seems like I don't know what I am doing, it's because I don't. I am trying to install firmware to my router and I'm just following the instructions. I appreciate your help.

I tried your command and I got:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
#

So my subnet is 192.168.1.0?

---

### Post by bab1 on 2012-04-05
> **unckybob said:**
> Thank you for the quick response. 

If it seems like I don't know what I am doing, it's because I don't. I am trying to install firmware to my router and I'm just following the instructions. I appreciate your help.

I tried your command and I got:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
#

So my subnet is 192.168.1.0?

Yes the network ID is 192.168.1.0 and the subnet mask is 255.255.255.0.

FYI: the network has 254 usable addresses from 192.168.1.1 to 192.168.1.254 The net ID (192.168.1.0) and the bcast address (192.168.1.255 should not be used).

See my other post for more information.

---

