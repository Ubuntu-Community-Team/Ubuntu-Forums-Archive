---
title: "Strange rural wireless connectivity problem"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Dzaaneez on 2010-01-22
I have a strange problem trying to connect a Dell laptop to the internet. It's running Ubuntu 9.10 Karmic. We live in a rural area and the only broadband available is long-distance wireless. Basically we have an antenna on the roof and that connects to a linksys router. When I boot the laptop into Windows it will connect to the router but not the internet until I "repair" the connection a couple times. Ubuntu, on the other hand, will never get the correct IP address and other info... no matter if I reconnect to the router multiple times or restart the computer. I have tried both wireless and wired connections to our router.

Here is the result of ifconfig:

> wlan0     Link encap:Ethernet  HWaddr 00:1c:df:5b:53:81  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe5b:5381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1543913 (1.5 MB)  TX bytes:34325 (34.3 KB)

In windows, the correct information should be a subnet mask of 255.255.252.0 and default gateway of 192.168.188.1. Ubuntu gets a subnet mask of 255.255.255.0 and a default route of 192.168.1.1.

I would really appreciate some help. Is there a dhcp conflict here? I have tried another router and had the same problem. The antenna on the roof receives power and I think might serve as a dhcp server in its own right. Perhaps the linksys router is conflicting with the antenna device? Thanks!

---

### Post by iponeverything on 2010-01-22
An easy solution would just configure network manager to use static IP with the correct information.

But, the issue appears to be with you linksys router. Is it yours or does it belong to the provider?

If it is yours double check its configuration. Make sure that the point-to-point addresses for radio link are not over-lapped by the DHCP range.   You might try using a different DHCP range anyway..

---

