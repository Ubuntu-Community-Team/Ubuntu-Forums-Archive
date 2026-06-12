---
title: "Wireless on Ubuntu 9.04 Broadcom 4328"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by asonda on 2009-08-14
Hi All,
 
Complete Linux noob here. Apologies.
 
I have a HP DV9665EA with a Broadcom 4328 Wireless Adaptor.
 
Inside Ubuntu, it says there is a Driver for the adaptor (restricted) and that it is enabled but is not currently in use.
 
I have been booting back into WIN7 and using my iPhone to to search the net, search the forums.
 
All I know and can tell you, then when I do a certain command I DON'T get 'wlan0' and I think I'm supposed to.
 
also the -C network shows that it knows the adaptor is there and is using a driver.
 
Could anybody try to help me?
 
Many Thanks

---

### Post by superprash2003 on 2009-08-14
post output of
1)iwconfig
2)ifconfig
3)sudo iwlist scanning

---

### Post by asonda on 2009-08-15
Hi,
 
Thanks for the reply :) Here are the results for what you asked...
 
 
1.) iwconfig


"lo no wireless extensions. 


eth0 no wireless extensions. 


pan0 no wireless extensions." 


2) ifconfig 


eth0 Link encap:Ethernet HWaddr 00:1b:24:be:fc:92 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:20 Base address:0x2000 


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 




3) sudo iwlist scanning 


lo Interface doesn't support scanning. 


eth0 Interface doesn't support scanning. 


pan0 Interface doesn't support scanning. 
 
 
 
Thanks

---

### Post by asonda on 2009-08-15
Right, I am now on the internet via wireless. I managed to get it working by using the b43-fcutter guide.

Thing is, when i do a ifcong i get this

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:195  Noise level:169
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0

pan0      no wireless extensions.



shouldn't eth1 be wlan?

Also, whilst i was trying stuff out yesterday, I followed something to open up a file via the terminal and change something from false to true?

---

### Post by BigCityCat on 2009-08-15
I have this driver and I have it working in ubuntu and kubuntu. In ubuntu I searched synaptic and installed b43-fwcutter. Then make sure the adapter is activated in hardware drivers provided by ubuntu.

If not that then maybe this post by me here. For Kubuntu

[http://ubuntuforums.org/showthread.php?t=1176117&page=4](http://ubuntuforums.org/showthread.php?t=1176117&page=4)

---

### Post by superprash2003 on 2009-08-17
also post output of **lshw -C network **

---

