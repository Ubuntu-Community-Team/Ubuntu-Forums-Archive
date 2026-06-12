---
title: "Unable to maintain network connection"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by ChrisRDixon on 2009-02-10
I am pretty new to Ubuntu, so please accept any lack of knowledge.

I am trying to rebuild an old windoze box with Ubuntu 8.10. The install seemed to go perfectly. It recognized my hardware, including the D-Link DGE550T network card. I was able to connect to the Internet and it found some 245 software updates. At some point in the downloading of the updates, it simply stopped retrieving them. I was unable to ping the router although it claimed I had a healthy network connection. I have run numerous tests (below) but am still unable to determine what is wrong. I checked the sys logs and, although there are some errors, the only one I see that pertains to a network issue was "Unable to locate IPV6 router".
I've made the following tests:
Replaced the ethernet cable with one from a working PC.
Swapped out the NIC with another that I know works.
Changed the port on the switch to one I know was working.
Reinstalled the system from scratch.
Tried copying files from the local network. It still craps out, but at random points. In other words it isn't failing after a specific number of seconds or a specific byte count of downloads.

Any help would be appreciated. For starters, how do I remove the IP6 settings? I cannot find any binding commands in the Network Manger utility.

---

### Post by superprash2003 on 2009-02-10
you could remove ipv6 this way [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html) .. also please post outpt of **ifconfig** from the terminal.. it could be an MTU problem

---

### Post by ChrisRDixon on 2009-02-10
I followed the steps to remove the IP6. It now appears that I have lost even the problematic network connection. Here is the output of ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

---

### Post by ChrisRDixon on 2009-02-10
There are, clearly, still some major bugs with the Networking in 8.10. Like many others on this site, and other forums, I do not have the "Network" utility under Administration. It shows as installed, but it isn't visible. Just one of the problems ...

I re-installed to 7.10 (as that was the only other install disk I had) and the networking worked just fine, so it isn't my hardware. From there I upgraded to 8.04 and that, also, works fine. 

I guess I will hold off 8.10 until the issues are fixed.

---

### Post by Neural oD on 2009-02-10
> **ChrisRDixon said:**
> There are, clearly, still some major bugs with the Networking in 8.10. Like many others on this site, and other forums, I do not have the "Network" utility under Administration. It shows as installed, but it isn't visible. Just one of the problems ...

I re-installed to 7.10 (as that was the only other install disk I had) and the networking worked just fine, so it isn't my hardware. From there I upgraded to 8.04 and that, also, works fine. 

I guess I will hold off 8.10 until the issues are fixed.
most of my network issues were sorted out when I went command line - those gui managers are a bit buggy at the moment. I know that cli isn't everyones cup of tea - but it sure is stable :)

---

