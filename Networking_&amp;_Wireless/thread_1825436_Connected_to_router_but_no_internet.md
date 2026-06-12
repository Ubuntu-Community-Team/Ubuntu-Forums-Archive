---
title: "Connected to router but no internet"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by s94linde on 2011-08-15
Hi,

I'm having a bit of a problem and I was hoping anyone out there could lend assistance.

I'm running a Natty machine wired to a TP-Link router (TL-WR841N) with additional Ubuntu and Windows machine on WiFi. Recently I've had some problems with connectivity on the Natty machine. Connectivity is fine as far as the router, but not beyond it. This applies to all browsers, Software Center, Aptitude and anything else you can think of. Now, normally at this point I would call my ISP, but the thing is, all other machines have connectivity. I've checked the cables twice and anyway, if it were them, I wouldn't be able to ping the router. Router has ping functionality to outside and it's working, have tried ubuntu.com and google.com. Also, connectivity between the wired and wireless machines is fine, pings are flying across the network beautifully.

So, to summarize: No internet connectivity for any applications on the wired machine, all is fine on the wifi machines, wired can still contact router. Any ideas?

---

### Post by imortalninja161 on 2011-08-15
hmmm yess no the normal situation i am assuming you have pinged the defualt gateway(router) from the system with the issue 

post resualts of ```
ifconfig
```

im starting to think it might be a router config issue

---

### Post by s94linde on 2011-08-15
eth0   Link encap:Ethernet HWAddr 20:cf:30:e3:93:4d
       inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
       inet6 addr: fe80::22cf:30ff:fee3:934d/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
       RX packets:14431 errors:0 dropped:0 overruns:0 frame:0
       TX packets:14526 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txquelen:1000
       RX bytes:8654451 (8.6 MB) TX bytes:1459640 (1.4 MB)
       Interrupt:40

As far as I can see, it looks alright. I've checked the router settings, and as far as I can see, all looks OK. The IP adress is DHCP and the correct adress is assigned, no ghosting and no other prominent issues. Not exactly sure what I should be looking for though...

---

### Post by imortalninja161 on 2011-08-15
hmmm :/ interesting try pinging google.com for instance that could rule out pc config issues also depending on your router but make sure the cable is in a Ethernet port not the "Internet port" and whats the model of your router man.
Also considering DHCP is enabled insure you have no more static addresses set

---

### Post by s94linde on 2011-08-15
Ninja, you're a genius! The problem was IP assignment caused by adding a smartphone to the network. It stole the IP assigned to the wired can. I reassigned the IP:s, everything up and running now. Thanks!

edit: Spoke too soon, it seemed to be working but it wasn't... Tried pinging google.com and ubuntu.com, no result. No apparent conflict in the DHCP settings, every device has an assigned IP on the network now.

The router is a TPLink model WR841N, firmware v3.12.5 build 100929.

---

### Post by s94linde on 2011-08-16
Solved, more or less. Router bug from what I can gather.

---

