---
title: "Connecting to internet via server"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by lcs81 on 2009-04-10
I would like to connect my ubuntu box to my company's internet. In my windows box, i have a user name and password whenever i start the Internet explorer. But not sure how to connect from ubuntu. 

Thanks

---

### Post by superprash2003 on 2009-04-10
look at the URL at IE's addressbar.. and type the same URL in firefox in ubuntu..and then try..

---

### Post by lcs81 on 2009-04-13
it does not work either.....

---

### Post by superprash2003 on 2009-04-13
post output of **ifconfig** from the terminal.

---

### Post by lcs81 on 2009-04-13
Here the ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:db:e7:fd  
          inet addr:172.22.33.15  Bcast:172.22.35.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:8cff:fedb:e7fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59986043 (57.2 MB)  TX bytes:2013607 (1.9 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:db:e7:06  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.0.0
          inet6 addr: fe80::21e:8cff:fedb:e706/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:570640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:122414 txqueuelen:1000 
          RX bytes:66319049 (63.2 MB)  TX bytes:263301955 (251.1 MB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:60:08:1c:54:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xe880 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208172 (203.2 KB)  TX bytes:208172 (203.2 KB)

-----------------------------------------------------------------

---

### Post by superprash2003 on 2009-04-14
does eth0 or eth1 get you to the internet? could you post a screenshot of the internet explorer login page in windows..

---

