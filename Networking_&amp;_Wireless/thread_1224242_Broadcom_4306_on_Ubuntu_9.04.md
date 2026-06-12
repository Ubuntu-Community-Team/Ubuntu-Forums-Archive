---
title: "Broadcom 4306 on Ubuntu 9.04"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Q-collective on 2009-07-27
Hello, I've installed Ubuntu 9.04 on my brothers' laptop and so far I've been unable to make his broadcom 4306 wireless chipset work. Or more precisely, it is being seen by the system, but it isn't able to scan for networks (as observed in the NetworkManager applet).

What I've done thusfar is to install fwcutter via system -> administration -> hardware drivers and restart the computer.

If I run ifconfig I get a confirmation my system sees wlan0:
```
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a4:87:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```So I'm puzzled as to what the exact problem is. Can anyone help me here?

---

