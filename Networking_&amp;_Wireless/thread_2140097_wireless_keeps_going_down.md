---
title: "wireless keeps going down"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by pickelhaupt on 2013-04-28
The wireless connection keeps going down on my windows laptop when my ubuntu laptop is on. It almost seems that my ubuntu laptop "kicks" the windows laptop off the home network. The ubuntu laptop seems to have priority or a "master" role compared to the windows laptop. The home network is a wireless D-Link DIR 600 connected to fibre. An IP telephone is connected to the switch part of the router.

I have limited network knowledge so I'm more or less in the dark here. Could it have something to do with IP addresses that the router hands out to the laptops? Is there anything in the network settings on the ubuntu laptop that could be the root? The ubuntu laptop is a Samsung 700 series gaming laptop running 12.04 LTS and the windows laptop is a Samsung 900 series running windows 8.

Any suggestions?

/K

---

### Post by gordintoronto on 2013-04-28
Have you done anything to use a static IP address on any of the devices? In the setup for your router, you should be able to specify the range of addresses handed out for DHCP connections. If you change the range, it might eliminate the problem. Static IP addresses should not be taken from the DHCP addresses. My router starts handing our DHCP addresses at 192.168.1.100, and this computer uses the static address 192.168.1.58 so there is never a problem.

---

