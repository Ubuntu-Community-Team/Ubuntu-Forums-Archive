---
title: "Same IP address at different locations on laptop"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by mikey.duhhh on 2009-04-18
Why would I get the same IP address at different locations on my Ubuntu 8.04 wireless laptop?  And how could I ensure it didn't always connect with the same IP?  

I'm not sure I want to connect to the same IP at a coffee shop, a restaurant, the open city network, etc., especially when I know they use different Internet providers. I first noticed this when using Conky to display the IP. 

How would I configure the machine to make these changes?  I'm using an Atheros wireless card (AR242x) with Madwifi and wondering if Madwifi is causing this. 

Part of the goodness of a laptop is that it should get different IP addresses, not the same IP when I am in a different spot.

---

### Post by PhrankDaChickenGeek on 2009-04-18
Are you sure Conky is displaying the correct address?
Typing the following command will tell your wireless card's IP address
```
ifconfig
```

At these WiFi spots, IP addresses are autocmatically given by the wireless Access Point via DHCP, not set internally by your laptop.

Maybe Conky is displaying the Access Point's IP, which may be the same at all locations

---

### Post by mikey.duhhh on 2009-04-19
> **PhrankDaChickenGeek said:**
> Are you sure Conky is displaying the correct address?

Maybe Conky is displaying the Access Point's IP, which may be the same at all locations

Yes.  I've checked it using ifconfig.  Conky is displaying correctly.

---

### Post by walkerk on 2009-04-19
Are all of these places using the same private subnet? I assume so. The first IP address DHCP assigns becomes your computers "Preferred IP". This means that every time your computer does a DHCP Request it asks for the preferred IP address. A DHCP server will offer this IP back as long as it is available. If not, it offers another address and your computer accepts the new address.

Your private IP address is not visible to the public.

Hope this helps.

---

### Post by bab1 on 2009-04-19
> **walkerk said:**
> Are all of these places using the same private subnet? I assume so. The first IP address DHCP assigns becomes your computers "Preferred IP". This means that every time your computer does a DHCP Request it asks for the preferred IP address. 
A DHCP server will offer this IP back as long as it is available. If not, it offers another address and your computer accepts the new address.

Your private IP address is not visible to the public.

Hope this helps.

This is not correct.  The host has to contact the **same** DHCP server that issued the DHCP lease to retain the same IP address.  It is the lease that stays the same (and therefore the IP address), not the just the IP address.  This is not to say that you can't by random be assigned a new lease from a different DHCP server with the same IP address.  But it  would be pure coincidence 

See [http://www.tcpipguide.com/free/t_DHCPLeaseLifeCycleOverviewAllocationReallocationRe.htm]("http://www.tcpipguide.com/free/t_DHCPLeaseLifeCycleOverviewAllocationReallocationRe.htm")

This is the pertinent part -- *" If a client already has an address from an existing lease, then when it reboots or starts up after being shut down, it will **[COLOR="Green"]contact the DHCP server that granted it the lease[/COLOR]** to confirm the lease and acquire operating parameters."*

---

