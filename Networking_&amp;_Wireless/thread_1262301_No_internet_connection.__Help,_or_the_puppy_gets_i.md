---
title: "No internet connection.  Help, or the puppy gets it!"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by eduardoeltortuga on 2009-09-09
My D-link DI-707p crapped out so I switched to an old, but unused Zonet (ZSR0104cp) broadband switch router I had in a box (wired). I have four machines hooked up to the router which is hooked up to a Comcast modem. I have XP, Ubuntu and Kubuntu and also a Mac. They all had internet connections with my D-link. 

     With the Zonet, I can connect to the internet with XP and Mac but not the Kubuntu or Ubuntu machines. I can share files between the computers, but no internet with Ubuntu/Kubuntu.

     I configured all the machines in the zonet system set-up wizard to the best of my ability.

ifconfig output:
[COLOR="Red"]eth0 [/COLOR]     Link encap:Ethernet  HWaddr 00:0c:76:4e:e6:46  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe4e:e646/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60663 (60.6 KB)  TX bytes:83185 (83.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:0c:76:4f:1e:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4372 (4.3 KB)  TX bytes:4372 (4.3 KB)

Also, I tried my Zonet power supply on the D-Link and it sprang to life! I don't know if this would be safe long-term because the output on the Zonet power supply is slightly higher (7.5V DC 700mA compared to +5.0V 2A on the D-link power supply.
     I have two questions. 
     How do I set-up the Zonet router for the Ubuntu/Kubuntu machines? 
     Would it be safe to switch power supplies?

                                  Thanks

P.S I don't really have a puppy

Wed 09 Sep 2009 04:28:12 PM MDT

---

### Post by Iowan on 2009-09-09
A 5-volt power supply *shouldn't* be too hard to find. Consider that the Zonet supply is 150% that of the D-Link - that doesn't sound long-term healthy.

(What is a puppy gonna do with a router, anyway???)

---

### Post by eduardoeltortuga on 2009-09-09
Thanks. I was going to try to find another power supply as you suggested. 
   I would still like to learn how to configure the Zonet unit to work Ubuntu/Kubuntu as it does with my Mac and PC.
                         Thanks

---

### Post by eduardoeltortuga on 2009-09-10
A little more help would be appreciated. 
                        Thanks

---

### Post by Iowan on 2009-09-10
Sorry, I have to work for a living, and management frowns on their equipment being used for "personal use". 
Check **route -n** to see if Ubuntu has the router as it's default gateway.
You can add a route with ```
sudo route add default gw routeraddress
``` to see if it works - it probably won't survive a reboot, though.

---

### Post by eduardoeltortuga on 2009-09-10
Thanks for getting back. Here is my route -n output:
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

 I'm not quite sure how to read this output to see if the router is the default gateway. When I bypass the router I can connect to the internet.
     By the way, I went to "The Shack" and they tested the power supply on the D-Link. It was bad but they wanted over $40 dollars for a new power supply and adapter. e-bay didn't have my model. Too bad because the others they had were running about $10 bucks.

---

