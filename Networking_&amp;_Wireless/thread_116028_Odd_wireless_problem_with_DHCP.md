---
title: "Odd wireless problem with DHCP"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by nickj6282 on 2006-01-11
Good evening,

I have a Dell laptop running Breezy with an Intel Pro/Wireless 2200 card. When I connect to a wireless network just about anywhere with DHCP it works well, and I can connect without a problem. When I connect at work, however, it's a different story. We're using a Cisco Aironet router and when I boot up with that network's ssid and WEP key already in the system, it won't connect or grab an IP address. I have to do a cycle of "sudo ifdown eth1; sudo ifup eth1", sometimes several cycles, before it will connect and grab an IP. I don't have this problem anywhere else, and other clients on the same network do not have this problem either. I don't know if my problem is with the PC or if it lies with the router. Does anyone have any suggestions or has anyone encountered a similar problem?

Thanks
-Nick

---

### Post by encompass on 2006-01-16
I have seen that too... try to disable your wired connection settings if any... and that fixed my problem.  I had an rtl8180 card.

---

### Post by nickj6282 on 2006-01-16
Yeah, my wired ethernet connection is not configured. I double checked. It's just weird how it only has a problem here at work and not anywhere else. At home, the library, mom's house, brother's house, girlfriend's house, all work without a hitch. But the office I have problems. Windows machines on the same network have no problem connecting to the wireless either, it's just the combination of this machine and that router for some reason.

---

