---
title: "Issues adding static route to etc/network/interfaces"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by BruceV on 2012-09-22
Hi,  I'm trying to add a permanent static route for a network connection to an embedded system. Initially I did it using the route command in terminal. The first problem I came across is that the command interpreter doesn't seem to like some switches that are referenced in the Ubuntu documentation. Also the netmask entry seems to cause problems. Here's the command I tried to enter:

route add -net 192.168.0.50 netmask 255.255.255.0 dev eth0. 

Does this look OK?

The second problem was when I tried to make the route permanent by adding it to /etc/network/interfaces. I added the following line to the file, also as explained in the Ubuntu doco...

up route add -net 192.168.0.50/24 dev eth0

This bricked the entire system when I restarted, I had to get back in via recovery mode. 

Altogether confused, any assistance would be appreciated.  TIA

---

### Post by oldos2er on 2012-09-22
Moved to Networking & Wireless.

---

### Post by The Cog on 2012-09-22
That doesn't work because the network address you give doesn't match the subnet mask you give. 
With a mask of 255.255.255.0, the address 192.168.0.50 is a host within network 192.168.0.0. 
If you give the network address rather than the host address, it works OK.
This command works: (no dot required after eth0):
```
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0
```

You are aware that it adds the named network as a local network, aren't you? 
It means that your PC will try to talk to the other address locally (same LAN) rather than using a default gateway as an intermediate router. Your other system may need similar configuration to tell it that your PC should be spoken to locally rather than via a default gateway. It's not that common to run two different networks on the same LAN, so I wonder if this is really what you want to achieve.

---

### Post by BruceV on 2012-09-30
Thanks, that's useful info for someone in my position - a real network newbie.

---

