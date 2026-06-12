---
title: "Ubuntu kills my network"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by jonny75904 on 2010-05-18
Hi all,



Internet Service: Consolidated
Type:  Ethernet with direct optic connection at the comms box
Wireless Router: DLink DIR-601

Wireless devices:
Toshiba Laptop with Vista
PlayStation 3

Wired devices:
Custom built machine with ubuntu 9.04, wired to router switch.  



In the past we have had problems with internet service outages.  I thought the issue was with the ISP, but now I think it may be ubuntu causing the problem.

For about the last month the ubuntu machine has been powered off - my wife had surgery so I haven't had much "play time."  

Today I booted it and within about 5 minutes the service dropped again, even for the laptop and PS3.  

ifconfig and ipconfig weren't working, even when bypassing the router.  Consolidated does not support linux, so we did the troublshooting with vista.  Ipconfig yielded weird configuration settings like subnet 255.255.224.0 and no gateway.  Everything was set to accept dynamic IP and DNS in the IPv4 configuration.

Nothing worked correctly until we powered off everything,  When vista booted I then had to reset the nic card for it to work again.

I think somehow my ubuntu machine is fudging it up for the rest of our devices,  These problems only seem to exist when ubuntu is up and running, and only happens intermittently. 

I am at a loss.  Can anyone give me advice as to what could be causing this to happen?

---

