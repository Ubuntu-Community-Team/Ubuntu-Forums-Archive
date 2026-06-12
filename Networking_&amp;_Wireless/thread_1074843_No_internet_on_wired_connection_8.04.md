---
title: "No internet on wired connection 8.04"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by decoy415 on 2009-02-19
Hey guys,

Been at this about 2 hours now and I've gotten nowhere. I'm running 8.04 and connected to the router by wire. The rest of the my local can get to the internet. I can ping the ubuntu box, I can even access my shared drive over the local network. But the ubuntu box can't ping anyone else accept the router, it can't access any webpages (on refresh firefox just returns quickly with the same "Page Load Error, Address Not Found"), and no network based apps will work correctly. Here's the ifconfig info:

```

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:95:6f:0e  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe95:6f0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1421980 (1.3 MB)  TX bytes:147882 (144.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26696 (26.0 KB)  TX bytes:26696 (26.0 KB)


```

If anyone can help you would be the awesomest-est-est evorz!!

Thanks in advance.

---

### Post by decoy415 on 2009-02-19
/bump

It started happening after I did a big update about a day ago. Is anyone else having this problem?

---

### Post by ccolbert on 2009-02-19
I was just getting ready to post the same issue. I'm completely new to Ubuntu and Linux. I didn't do an update, but have had this problem since the initial install (2 weeks ago). There are plenty of posts on how to fix the wireless connection issues, but I need to fix the wired first so the wireless troubleshooting can take place. Other than what decoy already posted, my system dual boots into Ubuntu and Windows 7 Beta (internet works fine in Windows). I also formatted and reinstalled the Ubuntu partition a second time with a wired connection in case there was some connection needed at install I may have missed the first time, but it was no help. Thanks in advance for any support!

---

