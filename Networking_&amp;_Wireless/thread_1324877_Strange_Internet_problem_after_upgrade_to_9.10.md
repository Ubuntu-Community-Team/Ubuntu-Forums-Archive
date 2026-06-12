---
title: "Strange Internet problem after upgrade to 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by klemencic on 2009-11-12
I have just upgrade to Ubuntu 9.10 and now having internet problems
When I start Firefox, my previous opened tabs will not load (connection problem error page comes up) but if I use the search box next to the address box I can search using Google and it returns results, but again I cannot connect to any of these sites

If I run Windows under VirtualBox, I have no troubles in browsing When I go back to Ubuntu, I can connect to any site which I looked at under windows

It may be something simply but still beyond me - any help appreciated


Following is the output from ifconfig

klem@klem:~$ ifconfig /all
/all: error fetching interface information: Device not found

klem@klem:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:7a:d0:9c
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::219:66ff:fe7a:d09c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5512 (5.5 KB)  TX bytes:14044 (14.0 KB)
          Interrupt:23 Base address:0xa000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by ZhuaSD on 2009-11-14
Its only FF that gives yuo trouble?  Maybe just re-install it...

Its usually the VB install that has trouble after upgrades.

You might want to install a fresh copy.  Just saying.

---

### Post by klemencic on 2009-11-17
Thanks I will give that a try
I am having some trouble with VB with the kernel not loading, but this corrects itself after a restart (sounds like the first law of Microsoft)

---

