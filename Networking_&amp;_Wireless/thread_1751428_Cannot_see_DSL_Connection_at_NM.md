---
title: "Cannot see DSL Connection at NM"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by azad on 2011-05-06
I had real trouble connecting to the internet with PPPoE over DSL. Then I came across pppoeconf and managed to get the internet working.

The computer connects to the internet on startup.


However, the DSL connection does not show on the NM applet. 


Here's a screenshot of the NM applet:
[http://i.imgur.com/mXUZP.png](http://i.imgur.com/mXUZP.png)


Here's a screenshot of the DSL Connection 1 settings:

[http://i.imgur.com/UDYm1.png](http://i.imgur.com/UDYm1.png)


Here's my ifconfig:


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4a:04:0e:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:a1:b0:60:de:5c  
          inet6 addr: fe80::2a1:b0ff:fe60:de5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1427458 (1.4 MB)  TX bytes:254615 (254.6 KB)
          Interrupt:23 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:203.190.6.138  P-t-P:203.190.6.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:1381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1387029 (1.3 MB)  TX bytes:219224 (219.2 KB)




Here's my /etc/network/interfaces :


auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual



How do I make the "DSL Connection 1" appear on the NM applet so I can enable/disable with mouse clicks?


Just to be clear, my internet *is working*. This is an issue with the NM applet.


Any light on the issue is greatly appreciated. Thanks in advance.

---

### Post by azad on 2011-05-17
Bump. Is this a bug with the Network Manager?

Network Manager fails to connect me via PPPoE over DSL, whereas pppoeconf can. So this must be a problem with NM.

Can anyone please look into this?

---

### Post by dineshs on 2011-05-18
According to the first screenshot you have two wired connections.Which device do you use to connect DSL? [COLOR="Blue"]eth0[/COLOR] (00:e0:4a:04:0e:f4 ) or [COLOR="Blue"]eth1[/COLOR] (00:a1:b0:60:de:5c) ?.
Under wired tab (in DSL connection1), ensure that the MAC address is the same as the ethernet device you are using to connect DSL.(If the MAC is wrong change it and run [COLOR="Blue"]sudo service network-manager restart[/COLOR]  )

---

### Post by azad on 2011-05-18
I am connecting via eth1 (00:a1:b0:60:de:5c)

I *do* have the MAC of eth1 set up as the MAC of DSL Connection 1.

But the DSL Connection does not show up in the applet.

---

### Post by dineshs on 2011-05-21
I think your eth1 is not managed by NM (first screenshot) since it is defined in /etc/network/interfaces.Can you edit /etc/network/interfaces to contain only the first two lines(loopback),restart and see?

---

