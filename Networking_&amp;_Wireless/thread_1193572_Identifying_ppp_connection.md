---
title: "Identifying ppp connection"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by HavocXphere on 2009-06-21
I've got an ADSL router in half-bridge mode. I want to know which of my 3 pppoe accounts is currently active. (I keep forgetting which one is dialled)

```
Havoc@Xphere:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XXXXXX
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146694 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:37401639 (37.4 MB)  TX bytes:14485882 (14.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46115 (46.1 KB)  TX bytes:46115 (46.1 KB)

**[COLOR="Red"][SIZE="4"]ppp0[/SIZE][/COLOR]**      Link encap:Point-to-Point Protocol  
          inet addr:196.210.206.240  P-t-P:196.210.142.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:324763 (324.7 KB)  TX bytes:1436 (1.4 KB)

**[COLOR="Red"][SIZE="4"]ppp1[/SIZE][/COLOR]**      Link encap:Point-to-Point Protocol  
          inet addr:196.210.218.233  P-t-P:196.210.142.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:17847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:15056901 (15.0 MB)  TX bytes:2395267 (2.3 MB)


```

I'd like to know the account names that go along with those marked connections.

Either the filename in /etc/ppp/peers (The name used when establishing the connection i.e. sudo pon XXXX), or the ADSL account name, i.e HavocX@MyISP will do.

Thanks

---

