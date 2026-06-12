---
title: "CONNECTION PROBLEM! Maybe my firewall..."
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by squareff255 on 2009-12-18
I installed dansguardian and everything was fine, but all of a sudden, it won't connect to the internet anymore. It's actually setup to connect through a wired ethernet connection that goes throughout my house, and when I plug the ethernet cable into the wall it says:```
Ifupdown (eth1)
Connection Established
```but the internet won't actually work.
I ran ifconfig and received this output:```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:14:20:b2  
          inet addr:10.8.16.1  Bcast:10.8.16.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe14:20b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1947 (1.9 KB)  TX bytes:19810 (19.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11980 (11.9 KB)  TX bytes:11980 (11.9 KB)

```So, it looks to me that the output of ifconfig is telling me that I should be connected to eth0. Is that true? If so, how do I tell it to connect to eth0? It won't show up on the list when I click on the network-manager-applet....

---

### Post by cgb on 2009-12-18
Are there other computers on your network that are still able to connect to the internet?  Its possible there is a problem with your router or modem although if there is other computers functioning fine on the network then this would not be the case.  Otherwise if everything is not working on other computers as well, try power cycling the router and even possibly the modem.

---

