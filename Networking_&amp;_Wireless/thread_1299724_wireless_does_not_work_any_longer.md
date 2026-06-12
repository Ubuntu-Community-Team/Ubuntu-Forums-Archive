---
title: "wireless does not work any longer"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by 10ghost on 2009-10-24
Hi readers,
Of recent i observed that my system was not seeing wireless network around.
I ran the command ifconfig to see the interface available. this gave me the output below.

[COLOR="Blue"][I]
     eth0      Link encap:Ethernet  HWaddr 00:1e:33:57:4a:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3367773641 overruns:0              	  frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1404 errors:0 dropped:0 overruns:0 			  carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70200 (68.5 KB)  TX bytes:70200 (68.5 KB)



[/I][/COLOR]

I also noticed that the Hardware drivers under system=>administration=>hardware drivers does not display anything unlike before.
What could be the problem and how can one troubleshoot such a problem?

---

### Post by 10ghost on 2009-10-24
i observed that the interface for wireless was not displayed when the command ifconfig was executed.
When first installed ubuntu my wireless was not working but i followed the Ndiswrapper troubleshooting guide whcih i used to resolve it then. Where i got a source code which i compiled on my system. 
After this it worked properly until recently when it stopped showing list of available adhoc and wireless network  around the area at the top right corner of my laptop.

---

### Post by 10ghost on 2009-10-24
i issued the command iwconfig and it displayed this

lo no wireless extensions.

eth0 no wireless extensions.

I hope this would help to resolve this problem

---

