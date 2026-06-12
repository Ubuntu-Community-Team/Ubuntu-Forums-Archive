---
title: "Cannot connect to internet"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by cindy5774 on 2011-11-01
Hello all. First, I am an absolute beginner so please bear with my lack of knowledge regarding Linux terminology, etc. I literally know nothing about Ubuntu - except that my internet will not work
 
Some facts: I was (and still am) running Windows XP and started having some issues and my boss had given me an Ubuntu 10.10 installation CD awhile ago so I finally decided to install it (along side Windows XP). For the record, I never had a problem getting online with XP. Once I installed 10.10, I had internet and was prompted to upgrade to 11.11, so I did. All of a sudden my wired network connection kept dropping for no reason but would come back up if I restarted. At some point it stopped altogether, so I stuck the 10.10 installation CD back in and reverted to the previous version. This did not help. I still cannot connect to the internet even with 10.10.
 
I've spent the last 3 days going through the Ubuntu forums and have literally tried everything to solve this problem but nothing is working. I even deleted Network Manager and tried just a static IP to no avail. I am currently connected to a router and tried connecting directly with just the modem and that didn't work either.
 
The problem is that I cannot get online with Ubuntu (I am currently on my laptop typing this thread) so I will not be able to copy and paste any outputs for you guys. What I do know is that the system is not finding "eth0". If I type "ifconfig" it does find an IP address. If I type "dhclient eth0" it says something about "No DHCPOFFERS received." and "No working leases in persistent database - sleeping." I'm at a loss here, so if anyone can help me I'd really appreciate it!

---

### Post by jonobr on 2011-11-01
Hello

Sounds like you have adone quite a few things so Im not exactly sure where you are.

It sounds as if your running configuration files rather then entwork manager, so, if that the case,
could you open a terminal window and 
type
```
ifconfig
```
and post the results

then

```
cat /etc/network/interfaces
```

and post the results

then

```
cat /etc/resolv.conf 
```

post the results

maybe even the results of 
```
dmesg | grep eth0 
```

this will hopefully show debug on your ethernet card.

```
lshw
```
will also tell us what network card your using

---

### Post by cindy5774 on 2011-11-01
Hello Father Jack, and thanks for helping me!  Here are the results you requested:
 
cindy@CindyUbuntu:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 00:18:f3:35:fe:71 
inet6 addr: fe80::218:f3ff:fe35:fe71/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:39 errors:0 dropped:4294967177 overruns:0 frame:0 
TX packets:37 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:3592 (3.5 KB) TX bytes:7381 (7.3 KB) 
Interrupt:20 Base address:0xdc00 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:571 errors:0 dropped:0 overruns:0 frame:0 
TX packets:571 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:57107 (57.1 KB) TX bytes:57107 (57.1 KB) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]cindy@CindyUbuntu:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]auto eth0 
iface eth0 inet static 
address 192.168.0.103 
netmask 255.255.255.0 
gateway 192.168.0.1 
cindy@CindyUbuntu:~$ cat /etc/resolv.conf 
nameserver 68.87.68.166 
nameserver 68.87.74.166 
[EMAIL="cindy@CindyUbuntu:~$"]cindy@CindyUbuntu:~$[/EMAIL] dmesg | grep eth0 
(note some of the top results got cut off)
[ 368.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 380.028067] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 392.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 404.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 416.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 428.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 440.028070] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 452.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 464.028061] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 476.028106] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 488.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 500.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 512.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 524.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 536.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 548.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 560.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 572.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 584.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 596.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 608.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 620.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 632.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 644.028060] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 656.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 668.028116] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 680.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 692.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 704.028065] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 716.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 728.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 740.028119] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 752.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 764.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 776.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 788.028116] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 800.028091] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 812.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 824.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 836.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 848.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 860.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 878.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 890.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 902.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 914.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 926.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 938.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 950.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1052.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1064.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1076.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1088.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1100.028097] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1112.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1124.028112] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1136.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1148.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1160.028240] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1172.028216] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1184.028235] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1196.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1208.028123] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1220.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1232.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1244.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1256.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1268.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1280.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1292.028218] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1304.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1316.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1328.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1340.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1352.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1364.028049] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1376.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1388.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1400.028121] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1412.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1424.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1436.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1448.028038] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1460.028069] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1472.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1484.028049] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1496.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1508.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1520.028080] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1532.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1544.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1556.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1568.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1580.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1592.028037] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1604.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1616.028064] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1628.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1640.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1652.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1664.028120] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1676.028037] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1688.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1700.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1712.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1724.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1736.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1748.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1760.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1772.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1784.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1796.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1808.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1820.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1832.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1844.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1856.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1868.028091] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1880.028091] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1892.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1904.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1916.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1928.028079] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1940.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1952.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1964.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1976.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 1988.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2000.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2012.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2024.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2036.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2048.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2060.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2072.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2084.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2096.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2108.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2120.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2132.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2144.028124] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2156.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2168.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2180.028081] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2192.028109] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2204.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2216.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2228.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2240.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2252.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2264.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2276.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2288.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2300.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2312.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2324.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2336.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2348.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2360.028090] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2372.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2384.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2396.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2408.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2420.028078] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2432.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2444.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2456.028064] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2468.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2480.028146] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2492.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2504.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2516.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2528.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2540.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2552.028068] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2564.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2576.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2588.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2600.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2612.028090] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2624.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2636.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2648.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2660.028034] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2672.028127] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2684.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2696.028033] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2708.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2720.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2732.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2744.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2756.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2768.028035] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2780.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2792.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2804.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2816.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2828.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2840.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2852.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2864.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2876.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2888.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2900.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2912.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2924.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2936.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2948.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2960.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2972.028091] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2984.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 2996.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3008.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3020.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3032.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3044.028098] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3056.028131] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3068.028115] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3080.028106] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3092.028082] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3104.028077] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3116.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3128.028091] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3140.028035] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3152.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3164.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3176.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3188.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3200.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3212.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3224.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3236.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3248.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3260.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3272.028106] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3284.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3296.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3308.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3320.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3332.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3344.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3356.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3368.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3380.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3392.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3404.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3416.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3428.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3440.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3452.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3464.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3476.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3488.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3500.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3512.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3524.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3536.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3548.028069] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3560.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3572.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3584.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3596.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3608.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3620.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3632.028068] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3644.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3656.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3668.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3680.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3692.028069] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3704.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3716.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3728.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3740.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3752.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3764.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3776.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3788.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3800.028067] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3812.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3824.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3836.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3848.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3860.028068] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3872.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3884.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3896.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3908.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3920.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3932.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3944.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3956.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3968.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3980.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 3992.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4004.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4016.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4028.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4040.028201] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4052.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4064.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4076.028184] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4088.028067] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4100.028165] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4112.028034] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4124.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4136.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4148.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4160.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4172.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4184.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4196.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4208.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4220.028062] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4232.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4244.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4256.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4268.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4280.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4292.028080] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4304.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4316.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4328.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4340.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4352.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4364.028212] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4376.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4388.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4400.028067] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4412.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4424.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4436.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4448.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4460.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4472.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4484.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4496.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4508.028068] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4520.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4652.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4664.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4676.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4688.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4700.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4712.028053] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4724.028097] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4736.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4748.028034] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4760.028079] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4772.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4784.028062] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4796.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4808.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4820.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4832.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4844.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4856.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4868.028075] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 4880.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5192.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5240.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5252.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5264.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5276.028048] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5288.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5300.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5312.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5324.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5486.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5528.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5540.028142] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5552.028039] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5564.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5576.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5588.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5600.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5612.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5624.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5636.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5648.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5660.028080] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5672.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5684.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5696.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5708.028070] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5720.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5732.028078] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5744.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5756.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5768.028080] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5780.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5792.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5804.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5816.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5828.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5840.028049] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5852.028040] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5864.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5876.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5888.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5942.028066] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 5978.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6002.028036] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6014.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6026.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6038.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6050.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6062.028064] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6074.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6404.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6452.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6464.028223] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6476.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6488.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6500.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6512.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6524.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6536.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6548.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6776.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6794.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6836.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6848.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6860.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6872.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6884.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6896.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 6908.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7202.028062] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7232.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7262.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7274.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7286.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7298.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7310.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7322.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7334.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7352.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7364.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7376.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7388.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7400.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7412.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7424.028062] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7436.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7448.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7460.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7472.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7484.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7496.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7508.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7520.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7532.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7544.028037] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7556.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7568.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7580.028041] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7592.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7604.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7616.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7628.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7640.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7652.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7664.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7676.028042] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7688.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7700.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7712.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7724.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 7736.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8000.028075] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8012.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8024.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8036.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8048.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8060.028043] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8102.028052] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8144.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8162.028178] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8174.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8186.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8198.028057] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8210.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8222.028110] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8234.028098] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8258.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8270.028063] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8282.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8294.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8306.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8318.028047] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8330.028056] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8342.028119] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8354.028051] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8366.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8378.028045] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8390.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8402.028060] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8414.028059] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8426.028050] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8438.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8450.028067] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8462.028060] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8474.028095] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8486.028046] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8498.028044] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8510.028144] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8522.028055] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8534.028062] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8546.028058] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[ 8558.028054] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF 
[EMAIL="cindy@CindyUbuntu:~$"]cindy@CindyUbuntu:~$[/EMAIL] 
cindy@CindyUbuntu:~$ lshw 
WARNING: you should run this program as super-user. 
cindyubuntu 
description: Computer 
width: 32 bits 
*-core 
description: Motherboard 
physical id: 0 
*-memory 
description: System memory 
physical id: 0 
size: 1948MiB 
*-cpu 
product: Intel(R) Celeron(R) M CPU 420 @ 1.60GHz 
vendor: Intel Corp. 
physical id: 1 
bus info: cpu@0 
version: 6.14.8 
serial: 0000-06E8-0000-0000-0000-0000 
size: 1600MHz 
width: 32 bits 
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm 
*-pci 
description: Host bridge 
product: ATI Technologies Inc 
vendor: ATI Technologies Inc 
physical id: 100 
bus info: pci@0000:00:00.0 
version: 01 
width: 64 bits 
clock: 66MHz 
configuration: latency=64 
resources: memory:0-1fffffff 
*-pci:0 
description: PCI bridge 
product: RS480 PCI Bridge 
vendor: ATI Technologies Inc 
physical id: 1 
bus info: pci@0000:00:01.0 
version: 00 
width: 32 bits 
clock: 66MHz 
capabilities: pci normal_decode bus_master cap_list 
resources: ioport:e000(size=4096) memory:fde00000-fdefffff memory:f0000000-f7ffffff 
*-display 
description: VGA compatible controller 
product: RC410 [Radeon Xpress 200M] 
vendor: ATI Technologies Inc 
physical id: 5 
bus info: pci@0000:01:05.0 
version: 00 
width: 32 bits 
clock: 66MHz 
capabilities: vga_controller bus_master cap_list rom 
configuration: driver=radeon latency=64 mingnt=8 
resources: irq:17 memory:f0000000-f7ffffff ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff 
*-ide:0 
description: IDE interface 
product: IXP SB400 Serial ATA Controller 
vendor: ATI Technologies Inc 
physical id: 12 
bus info: pci@0000:00:12.0 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: ide bus_master cap_list rom 
configuration: driver=sata_sil latency=64 
resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f1ff memory:fdf80000-fdffffff 
*-usb:0 
description: USB Controller 
product: IXP SB400 USB Host Controller 
vendor: ATI Technologies Inc 
physical id: 13 
bus info: pci@0000:00:13.0 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: ohci bus_master cap_list 
configuration: driver=ohci_hcd latency=64 
resources: irq:19 memory:fe02e000-fe02efff 
*-usb:1 
description: USB Controller 
product: IXP SB400 USB Host Controller 
vendor: ATI Technologies Inc 
physical id: 13.1 
bus info: pci@0000:00:13.1 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: ohci bus_master cap_list 
configuration: driver=ohci_hcd latency=64 
resources: irq:19 memory:fe02d000-fe02dfff 
*-usb:2 
description: USB Controller 
product: IXP SB400 USB2 Host Controller 
vendor: ATI Technologies Inc 
physical id: 13.2 
bus info: pci@0000:00:13.2 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: ehci bus_master cap_list 
configuration: driver=ehci_hcd latency=64 
resources: irq:19 memory:fe02c000-fe02cfff 
*-serial UNCLAIMED 
description: SMBus 
product: IXP SB400 SMBus Controller 
vendor: ATI Technologies Inc 
physical id: 14 
bus info: pci@0000:00:14.0 
version: 83 
width: 32 bits 
clock: 66MHz 
configuration: latency=0 
resources: ioport:b00(size=16) memory:fe02b000-fe02b3ff 
*-ide:1 
description: IDE interface 
product: IXP SB400 IDE Controller 
vendor: ATI Technologies Inc 
physical id: 14.1 
bus info: pci@0000:00:14.1 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: ide bus_master cap_list 
configuration: driver=pata_atiixp latency=64 
resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16) 
*-multimedia 
description: Audio device 
product: IXP SB4x0 High Definition Audio Controller 
vendor: ATI Technologies Inc 
physical id: 14.2 
bus info: pci@0000:00:14.2 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: bus_master cap_list 
configuration: driver=HDA Intel latency=64 
resources: irq:40 memory:fe024000-fe027fff 
*-isa 
description: ISA bridge 
product: IXP SB400 PCI-ISA Bridge 
vendor: ATI Technologies Inc 
physical id: 14.3 
bus info: pci@0000:00:14.3 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: isa bus_master 
configuration: latency=0 
*-pci:1 
description: PCI bridge 
product: IXP SB400 PCI-PCI Bridge 
vendor: ATI Technologies Inc 
physical id: 14.4 
bus info: pci@0000:00:14.4 
version: 80 
width: 32 bits 
clock: 66MHz 
capabilities: pci subtractive_decode bus_master vga_palette 
resources: ioport:d000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff 
*-network 
description: Ethernet interface 
product: RTL-8139/8139C/8139C+ 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 2 
bus info: pci@0000:02:02.0 
logical name: eth0 
version: 10 
serial: 00:18:f3:35:fe:71 
width: 32 bits 
clock: 33MHz 
capabilities: cap_list ethernet physical 
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=0 maxlatency=64 mingnt=32 multicast=yes 
resources: irq:20 ioport:dc00(size=256) memory:fddff000-fddff0ff 
*-communication UNCLAIMED 
description: Communication controller 
product: HSF 56k Data/Fax Modem 
vendor: Conexant Systems, Inc. 
physical id: 5 
bus info: pci@0000:02:05.0 
version: 00 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list 
configuration: latency=64 
resources: memory:fdde0000-fddeffff ioport:df00(size=8) 
*-firewire 
description: FireWire (IEEE 1394) 
product: FW322/323 
vendor: Agere Systems 
physical id: 6 
bus info: pci@0000:02:06.0 
version: 70 
width: 32 bits 
clock: 33MHz 
capabilities: ohci cap_list 
configuration: driver=firewire_ohci latency=0 maxlatency=24 mingnt=12 
resources: irq:21 memory:fddfe000-fddfefff 
*-scsi 
physical id: 1 
bus info: scsi@0 
logical name: scsi0 
capabilities: scsi-host 
configuration: driver=usb-storage 
cindy@CindyUbuntu:~$

---

### Post by cindy5774 on 2011-11-01
Oh, and as for my network card, would that be the "Ethernet Controller"?  If so, it is a Realtek 8139.  Thanks!

---

### Post by jonobr on 2011-11-02
It seems yoiur eth0 comes up but the ip address is never assigned to it
When you run ifconfg you should see tyhe ip address in the result for eth0

Under the face eth0 inet static 
line
I would also add these pieces

```

address 192.168.0.103 
netmask 255.255.255.0 
gateway 192.168.0.1 
**network 192.168.0.0**
**broadcast 192.168.0.255**
```

Then restart networking.

```

sudo /etc/init.d/networking restart
```
you should be able to then ping 192.168.0.103
and then 192.168.0.1



Also , did you remove network manager?

When you configure the /etc/network/interface file directly, then
network manager doesnt control your interface card

---

### Post by jonobr on 2011-11-02
P.s. I love my brick!!!!!!!!!

---

### Post by cindy5774 on 2011-11-02
IT WORKED!!!  Yes, I uninstalled Network Manager and followed the directions in this link: [http://www.webupd8.org/2009/06/how-to-manually-set-up-your-wired.html](http://www.webupd8.org/2009/06/how-to-manually-set-up-your-wired.html). But it didn't say anything about adding lines for network and broadcast.  That totally did the trick. Thank you soooooooo much!!  DRINK!
 
P.S. - Will I ever be able to install Network Manager again?  I kinda liked it.

---

### Post by jonobr on 2011-11-02
Yep

I think its a sudo apt-get install network-manager-gnome or something close to that.

Once you do this remember you cant modified files directly

NM should look after that.

I dont use NM as I found/find it flakey from upgrade to upgrade, so I just got used to modifying the network config files myself

**** off

Jonobr

---

### Post by cindy5774 on 2011-11-02
Wait - it seems my excitement may have been premature.  The internet only works while "ping 192.168.0.103" is running.  When I close the Terminal, I go offline.  Any ideas as to what that's that all about?

---

### Post by jonobr on 2011-11-02
open a couple of terminals

in one
ping 192.168.0.103

in the second 
ping 192.168.0.1

in the third

ping 216.92.151.75

and in a fourth ping pingplotter.com

leave them run a while see if any drop.

Have you got this line in your config?
```
broadcast 192.168.0.255
```

There may be an arp issue where the mac address is written out of the arp table and thing may not know how to issue an arp without that line, just a guess on my part.

Lastly

If it keeps droping 
take a look at 
```
dmesg | grep eth
```

The original one you did showed the Ethernet connection was up.
Its its flakey you should that its down at points

---

### Post by cindy5774 on 2011-11-02
OK.  ping 192.168.0.103 just keeps on pinging and says nothing about dropping.
 
ping 192.168.0.1 keeps saying "Destination Host Unreachable"

ping 216.92.151.75 keeps saying "From 192.168.103 ....Destination Host Unreachable"

ping pingplotter.com says "unknown host pingplotter.com"
 
dmesg | grep eth says on every line "eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF"

I do have broadcast 192.168.0.255 in my config.

---

### Post by jonobr on 2011-11-02
Are you sure 192.168.0.1 is your gateway?

Can you ping from another device to ubuntu?

maybe also if you could post ifconfig again

---

### Post by cindy5774 on 2011-11-02
I believe the gateway is correct.  That's what it says when I do an ipconfig on my Windows-based laptop (it says "Default Gateway....192.168.0.1) , and that's what I type to reach the router settings.  Is there another way to check?
 
Here are the results from ifconfig:
 
cindy@CindyUbuntu:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 00:1f:16:59:13:4c 
inet addr:192.168.0.103 Bcast:192.168.0.255 Mask:255.255.255.0 
inet6 addr: fe80::21f:16ff:fe59:134c/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:16 errors:0 dropped:4294965031 overruns:0 frame:0 
TX packets:32 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:1058 (1.0 KB) TX bytes:5250 (5.2 KB) 
Interrupt:20 Base address:0xdc00 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:52613 errors:0 dropped:0 overruns:0 frame:0 
TX packets:52613 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:4731832 (4.7 MB) TX bytes:4731832 (4.7 MB) 
 
Here are some results from pinging 192.168.0.103 within Ubuntu:
cindy@CindyUbuntu:~$ ping 192.168.0.103 
PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data. 
64 bytes from 192.168.0.103: icmp_req=1 ttl=64 time=0.042 ms 
64 bytes from 192.168.0.103: icmp_req=2 ttl=64 time=0.031 ms 
64 bytes from 192.168.0.103: icmp_req=3 ttl=64 time=0.042 ms 
64 bytes from 192.168.0.103: icmp_req=4 ttl=64 time=0.036 ms 
64 bytes from 192.168.0.103: icmp_req=5 ttl=64 time=0.039 ms 
64 bytes from 192.168.0.103: icmp_req=6 ttl=64 time=0.049 ms 
64 bytes from 192.168.0.103: icmp_req=7 ttl=64 time=0.036 ms 
64 bytes from 192.168.0.103: icmp_req=8 ttl=64 time=0.028 ms 
64 bytes from 192.168.0.103: icmp_req=9 ttl=64 time=0.038 ms 
64 bytes from 192.168.0.103: icmp_req=10 ttl=64 time=0.037 ms 
64 bytes from 192.168.0.103: icmp_req=11 ttl=64 time=0.044 ms 
64 bytes from 192.168.0.103: icmp_req=12 ttl=64 time=0.047 ms 
64 bytes from 192.168.0.103: icmp_req=13 ttl=64 time=0.036 ms 
64 bytes from 192.168.0.103: icmp_req=14 ttl=64 time=0.034 ms 
64 bytes from 192.168.0.103: icmp_req=15 ttl=64 time=0.035 ms 
64 bytes from 192.168.0.103: icmp_req=16 ttl=64 time=0.038 ms 
64 bytes from 192.168.0.103: icmp_req=17 ttl=64 time=0.029 ms 
64 bytes from 192.168.0.103: icmp_req=18 ttl=64 time=0.042 ms 
64 bytes from 192.168.0.103: icmp_req=19 ttl=64 time=0.038 ms 
64 bytes from 192.168.0.103: icmp_req=20 ttl=64 time=0.032 ms 
64 bytes from 192.168.0.103: icmp_req=21 ttl=64 time=0.038 ms 
 
But when I tried pinging 192.168.0.103 from my Windows-based laptop, it said "Destination Host Unreachable".

---

### Post by jonobr on 2011-11-02
Hello

The ip address is bound to your nic, the stack is operational and able to ping,
it says your eth0 is active and up in dmesg,
this is ready to work,

did you check your cable as Im wondering if either you have a bad cable or a bad port on your router.

Something is out of order here -
and just for good measure, if you could report the current version of 

/etc/network/interfaces for me

---

### Post by jonobr on 2011-11-02
One other thing I would do if it was my box,

I would disable IPV6
To check IPv6 status

```
 cat /proc/sys/net/ipv6/conf/all/disable_ipv6 
```



a returned 0 means it&#8217;s enabled and 1 &#8211; disabled.. if you get the 1, leave as is.



To disable IPv6, go to the command line  paste this in a terminal:

```
 echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf

echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

```
(PASTE IN EACH LINE ONE AT A TIME!!!!)

reboot and check IPv6 has been disabled

---

### Post by cindy5774 on 2011-11-02
Hello.  I logged back into Windows XP (because this is a dual boot) to look at the IP settings and the IP address seems to have changed to 192.168.0.104 (I could swear it was 192.168.0.103 earlier).  Anyway, I changed the IP address in Ubuntu and all seems to be working fine now. Thanks so much for all your help!!
 
-Cindy

---

### Post by jonobr on 2011-11-03
mmmmmm

I remain unconvinced,

I think you have an intermittent problem  with your dual boot.
there is no real difference between using 103 and 104.
Lets hope it stays working, but again, im getting the feeling ti will stop working for you at some point.

Hopefully Im wrong:D

---

