---
title: "eth0 and wlan0 connect to same subnet"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2011-02-10
When I start my pc with a wired and wireless connection, I get ip addr on both. 

Same subent:
192.168.1.112 eth0
192.168.1.81 wlan0

I can ping the gateway, I can ping any device on the network but I can not ping beyond the gateway (yahoo.com) unless I ifdown either eth0 or wlan0.  

What I am trying to do during boot is if eth0 is not active (unpluged) to just start wlan0. If I set up different netmask for each adapter on the same subnet, would that be the way to go or can I add something to network/interfaces?

I think I might be able to use the package ifplugd, but I am unfamilar with that.  Anyone using ifplugd for this purpose, or using a script? 

I think maybe a script that would check if eth0 is active, if not than start wlan0, but wlan0 would be nice for it to check my wpa2 work connection, my wep home connection or an open unsecure connection in that order.  I guess a script is maybe what i need to provide me with flexibility but not sure.

Looking for a little advice and direction from someone using something similar.

Thank you

---

