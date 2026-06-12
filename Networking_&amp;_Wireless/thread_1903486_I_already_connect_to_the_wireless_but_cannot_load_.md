---
title: "I already connect to the wireless but cannot load any web pages"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by mike_kzc on 2012-01-02
I just installed a ubuntu 11.10 in my pc about a week ago, and the wireless network works perfectly until yesterday.   
 

When I turn on my computer, I have to wait about ~30 minutes before I can connect to any website. I think my pc already connect to the Internet, I even can see &#8220;Signal bar&#8221; on the upper right corner, but whenever I am opening any website, it gives me this: (btw, I am using our school's wireless)


 *********************
 The connection was interrupted
 

 The connection to wireless.csu.edu was interrupted while the page was loading.
 

 The site could be temporarily unavailable or too busy. Try again in a few
     moments.
   If you are unable to load any pages, check your computer's network
     connection.
   If your computer or network is protected by a firewall or proxy, make sure
     that Firefox is permitted to access the Web.
 **************************
 

 Next I use &#8220;ifconfig&#8221;, here is the information,
 

 ******************************
  eth0      Link encap:Ethernet  HWaddr 00:21:9b:e1:a6:d7   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:16  
 

 eth1      Link encap:Ethernet  HWaddr 00:22:69:31:ee:d7   
           inet addr:144.174.231.26  Bcast:144.174.231.255  Mask:255.255.252.0  
           inet6 addr: fe80::222:69ff:fe31:eed7/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           **RX packets:150 **errors:0 dropped:0 overruns:0 frame:339  
           TX packets:179 errors:16 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:38012 (38.0 KB)  TX bytes:25724 (25.7 KB)  
           Interrupt:17 Base address:0xc000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 ******************************
 

 One thing I notice is that: the number after the &#8220;RX packets :**150**&#8221; in eth1 keeps increasing, until it becomes much larger (like 3000), the wrong information is gone and I can see any webpage. But the problem is: it takes ~30 minutes to reach that larger number.  
 

 And then, &#8220;ifconfig&#8221; give me this:
 ****************************************
 eth0      Link encap:Ethernet  HWaddr 00:21:9b:e1:a6:d7   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:69:31:ee:d7   
           inet addr:144.174.231.26  Bcast:144.174.231.255  Mask:255.255.252.0 
           inet6 addr: fe80::222:69ff:fe31:eed7/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3271 errors:0 dropped:0 overruns:0 frame:254687 
           TX packets:1721 errors:110 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:562404 (562.4 KB)  TX bytes:248073 (248.0 KB) 
           Interrupt:17 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:726 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:726 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:54860 (54.8 KB)  TX bytes:54860 (54.8 KB) 
 *****************************************

 Does anyone know what is going on and how to fix it. Please help. Thanks in advance.

---

