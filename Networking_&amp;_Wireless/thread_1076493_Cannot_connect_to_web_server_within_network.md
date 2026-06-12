---
title: "Cannot connect to web server within network"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by R.Bucky on 2009-02-21
I have a home network with Ubuntu server 8.04 and Ubuntu-Desktop through a router and static ip. The problem is that I cannot view portions of my web site (I am the host) within the network. Only the text on my Wordpress blog is visible - no css or images. My [Concrete5]("http://www.concrete5.org") main web pages do not show up at all (404 error). However, my [Glype proxy]("http://buckycomputing.net/proxy/"), hand coded php and [html pages]("http://buckycomputing.net/hulu.html") show up just fine. 

I have port forwarded 80 on the router, opened up ufw to allow connections from my server to this other ubuntu box using the internal ip (e.g. 10.1.10.1). Also, I cannot visit my domain name on the internal network because it produces a 404. I have to use the internal ip to visit any of the above mentioned pages. Any thoughts on this issue?

---

### Post by superprash2003 on 2009-02-21
go to the command prompt and type ifconfig and post output..

---

### Post by R.Bucky on 2009-02-21
Thanks for your response superprash - here it is.

```
eth0      Link encap:Ethernet  HWaddr 00:40:ca:9e:12:a9  
          inet addr:10.1.10.122  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe9e:12a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:158804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15772743 (15.0 MB)  TX bytes:162924717 (155.3 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8174431 (7.7 MB)  TX bytes:8174431 (7.7 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.116.1  Bcast:192.168.116.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.76.1  Bcast:192.168.76.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by superprash2003 on 2009-02-22
you cannot use your Domain Name to access your website if you are hosting it on the same network.. you have to use its internal ip address..

---

### Post by R.Bucky on 2009-02-22
I connect to other portions of my server using the 10.1.10.XX address only. However, when I connect I can see that it is looking for my domain name instead of the local address. This only occurs on my Worpdress and Concrete5 pages. Otherwise, my proxy server and other pages are smokn' fast and resolved perfectly.

---

