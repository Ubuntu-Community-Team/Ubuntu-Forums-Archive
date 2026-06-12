---
title: "network connection"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by mhilinski on 2009-04-12
how do i check the nework connection to see if it is workng or not?

---

### Post by dmizer on 2009-04-13
Open a web browser and see if you can view a page.
Open a terminal and try to ping a url
```
ping www.google.com
```
Open a terminal and see if you have an IP address
```
ifconfig
```
This will give you an output that looks like
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:ff:75:39:d3:c1  
          [COLOR="Red"]inet addr:10.0.2.15[/COLOR]  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34379871 (32.7 MB)  TX bytes:277107634 (264.2 MB)
          Interrupt:2 
```
(IP address highlighted in red)

---

