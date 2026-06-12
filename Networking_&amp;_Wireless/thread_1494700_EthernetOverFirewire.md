---
title: "EthernetOverFirewire"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by walidus on 2010-05-27
I try do lan like in
[https://help.ubuntu.com/community/EthernetOverFirewire](https://help.ubuntu.com/community/EthernetOverFirewire)

and the problem:

ifconfig shows no additional eth, but ifconfig -a show

eth1      Link encap:UNSPEC  HWaddr 00-1B-24-00-00-5E-E2-1B-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9334 (9.3 KB)

sudo ifconfig eth1 192.168.1.2 up
sudo ifconfig eth1 192.168.1.1 up (on second computer)

ping 192.168.1.1 not working..
ping 192.168.1.2 working

Link encap:UNSPEC - I guess this should be Ethernet?

Modules are..
walidus@walidus-laptop:~$ lsmod|grep 1394
eth1394                13318  0 
ohci1394               26950  0 
ieee1394               81181  2 eth1394,ohci1394

What can be wrong?

---

