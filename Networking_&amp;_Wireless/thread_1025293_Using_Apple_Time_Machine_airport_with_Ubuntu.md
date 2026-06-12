---
title: "Using Apple Time Machine airport with Ubuntu"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by debeyt on 2008-12-29
I am having problems connecting my wired desktop Ubuntu machine to the Internet. Using the Network Tools, I can ping many sites on the Internet but cannot connect FireFox to the outside world. When attempting to connect to a site - e.g. [www.google.ca](www.google.ca), it will sit for hours attempting to make a connection. It will not time out or provide any other message.

Ifconfig supplies the following:
tom@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:50:4b:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:a0:cc:34:a7:9d  
          inet addr:10.0.1.148  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe34:a79d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12524 errors:5725 dropped:0 overruns:0 frame:5889
          TX packets:124296 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1258470 (1.2 MB)  TX bytes:12277258 (12.2 MB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36200 (36.2 KB)  TX bytes:36200 (36.2 KB)

This disconnect occurred after two events. 1. My original Time Machine crapped out and was replaced with a new one, and 2. I installed Ubuntu 10.10. Previously, my connection worked fine. I also have several MacBooks and a PowerMac connected wirelessly without any problems. I have also tried connecting them by wire and again no problem.

Any ideas any one? Any assistance would be greatly appreciated.

---

