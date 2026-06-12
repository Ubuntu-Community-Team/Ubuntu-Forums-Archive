---
title: "internet connection problem"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by arpit@aligator on 2008-12-12
i have problem in connecting to internet
when i type ifconfig in ubuntu 8.10 i get the following message

arpit@aligator:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:94:5a:06  
          inet addr:116.72.191.215  Bcast:116.72.191.255  Mask:255.255.240.0
          inet6 addr: fe80::221:70ff:fe94:5a06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41182 errors:0 dropped:2488804158 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2517245 (2.5 MB)  TX bytes:978 (978.0 B)
          Interrupt:218 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:12:7f:bd  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76700 (76.7 KB)  TX bytes:76700 (76.7 KB)

when i typed sudo pppoeconf i get the following message
Sorry, I scanned 2 interfaces, but the Access        
           Concentrator of your provider did not respond. Please  
           check your network and modem cables. Another reason     
           for the scan failure may also be another running pppoe  
           process which controls the modem.           
          

how can i connect to the internet?
i'm using broadband cable connection.. please help

---

### Post by superprash2003 on 2008-12-12
did you use a dialer to connect to the internet in windows ?

---

### Post by arpit@aligator on 2008-12-12
yes  i used it 
it works in windows but not in ubuntu

and i'n unable to understand why it is saying '..another running pppoe  
           process which controls the modem'

---

### Post by superprash2003 on 2008-12-13
in that case type poff and then try sudo pppoeconf

---

