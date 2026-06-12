---
title: "Encore  Wireless Network Problem"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by pabloKane on 2010-08-10
Hello, I installed Ubuntu 10.4 LTS and everything its fine, but I can´t join my computer to my wireless network.
I have an Encore ENLWI-G card and It doesn't work, How can I make it works. I have a router with WPA-Personal Security and MAC filter.
I'm really new with Ubuntu.

Thanks

---

### Post by MasterGamerJK on 2010-08-10
please run ifconfig in a terminal and post results so that we can better assist you, also make sure that you configured the  MAC filtering on your router properly with the correct  MAC address form the ubuntu box

---

### Post by pabloKane on 2010-08-10
Yes, I have Windows XP installed too and the wireless it's working.

This is the result of ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:d3:5a:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

---

