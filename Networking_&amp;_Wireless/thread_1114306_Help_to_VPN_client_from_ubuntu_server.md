---
title: "Help to VPN client from ubuntu server"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by emjay86 on 2009-04-02
Hi guys.. 

I'm just trying to figure out to get a VPN tunnel to relakks.com running from my Ubuntu server.

I'm using pppd to establish the connection. I've managed to get the connection running but I cant route my default connection to the tunnel.. I think I got a Routing problem since the transmit rate on the tunnel connection just goes crasy..

I've tried this out

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data)

but it does not make a bigger difference. My netstat -rn when connected looks like this 

[I]Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
93.182.169.2    0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.192 U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0[/I]

my ifconfig looks like this
[I]
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:93.182.169.59  P-t-P:93.182.169.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1375282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:13011 (12.7 KB)  TX bytes:695334128 (663.1 M[/I]B)

Got any ideas for my little project here (: ? thx

---

