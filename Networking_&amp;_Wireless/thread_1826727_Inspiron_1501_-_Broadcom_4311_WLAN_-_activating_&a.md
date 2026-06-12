---
title: "Inspiron 1501 - Broadcom 4311 WLAN - activating &amp; enabling"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by KaizersOrchestra on 2011-08-17
I've been working on getting wireless up on 11.04 for 3 days but no avail.  For some reason there is NO wireless connection recognized at all.

ifconfig yields:
```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:c5:b5:1e  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fec5:b51e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3777446 (3.7 MB)  TX bytes:342501 (342.5 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)
```iwconfig yields:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```lspci -nn | grep 0280  yields:
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```I have the proprietary Broadcom STA driver installed and activated.  What I need to do is first make there be a wlan0 somewhere, then turn on my card, then connect to a network.  I've tried many suggestions on these forums but none of them have worked so far.  Please help?

---

### Post by bkratz on 2011-08-17
Please see this page. Post back if problems

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by KaizersOrchestra on 2011-08-17
Thanks a lot, for future reference that link should definitely be in the sticky about Broadcom 43xx cards, I was unable to find any solution as good as this one!

---

### Post by bkratz on 2011-08-17
> **KaizersOrchestra said:**
> Thanks a lot, for future reference that link should definitely be in the sticky about Broadcom 43xx cards, I was unable to find any solution as good as this one!

Glad it helped you. This is a recent project from some of the best minds in this forum. You will see that Chili555 was the main contributor to this one. Please return to the thread tools at the top of the page and mark the thread solved in case it helps someone else.

---

