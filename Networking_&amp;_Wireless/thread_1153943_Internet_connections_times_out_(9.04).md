---
title: "Internet connections times out (9.04)"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by nhambrecht on 2009-05-09
Hi there,
I got a rather strange problem with my internet connection on Ubuntu 9.04. It works for about five minutes (usually on the first boot of a day), the rest of the time my queries take forever or I get timeouts. Funny enough, google works almost every time and ICQ (Pidgin) doesn't have problems at all. I allready tried multiple DNS-Servers, but that did not fix the problem. A traceroute to common hosts such as heise.de revealed that the problem seem to be timeouts far beyond the local network or my provider. But the same computer with windows connects fine and no other machine in the network has problems like this.
My only idea was IPv6, so I disabled it in firefox, but it still refuses to connect properly.

In case of heise.de the last (working) connection is two or three jumps after I left the network of my provider, with ubuntuforums.org its more than ten steps away.

I have absolutely no clue. The system is almost unchanged, only the automatic updater ran every day.

Thanks in advance.

---

### Post by superprash2003 on 2009-05-09
post output of ifconfig from the terminal.. could be an MTU related issue

---

### Post by nhambrecht on 2009-05-09
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2b:4b:4a  
          inet addr:141.28.226.157  Bcast:141.28.227.255  Mask:255.255.254.0
          inet6 addr: fec0::9:222:15ff:fe2b:4b4a/64 Scope:Site
          inet6 addr: 2002:8d1c:e25e:9:222:15ff:fe2b:4b4a/64 Scope:Global
          inet6 addr: fe80::222:15ff:fe2b:4b4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:658 errors:9 dropped:0 overruns:0 frame:9
          TX packets:499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49635 (49.6 KB)  TX bytes:39914 (39.9 KB)
          Interrupt:19 Base address:0xdead 

```

Do you need the output of the other devices as well? I got wlan0, wmaster0, and of course, lo.

---

### Post by superprash2003 on 2009-05-10
you should also consider disabling ipv6 in ubuntu as well.. here's a small guide [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by nhambrecht on 2009-05-10
Disabling IPv6 did not work (If I remember correctly the ipv6 module is built into the kernel and can not be disabled without rebuilding a 'custom kernel'), however I read the blog a little further and stumbled across [this]("http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html"). So I executed "$: sudo ifconfig eth0 mtu 1492" and now everything works just fine. Thanks!

---

