---
title: "wlan settings"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by dmubu on 2011-07-28
Hello,

I was fooling with my ifconfig settings in order to change mode to promiscuous.

I ran the following command:

sudo ifconfig wlan1 prmisc

This worked, but now I cannot connect to the internet.  How can restore my previous wlan settings, namely, go back to managed mode?

I ran this:
iwconfig wlan1 mode managed

and received this:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Operation not permitted.

Any suggestions?

Thank you so much!

---

### Post by dmubu on 2011-07-28
I ran the following command and the connection is back:

sudo ifconfig wlan1 -promisc

However, when I ran ifconfig originally, it stated that I was in managed mode.  Now, the output reads:

wlan1     Link encap:Ethernet  HWaddr 00:1f:e1:0e:d9:4c  
          inet6 addr: fe80::21f:e1ff:fe0e:d94c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4663487 (4.6 MB)  TX bytes:1259961 (1.2 MB)


Is this the right setting?

Thank you

---

