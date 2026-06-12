---
title: "Slow speed when sending to Ubuntu 11.04"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by patpicos on 2011-10-21
Hi all. 

I am experiencing issues sending at full GBit speed across my lan to my Ubuntu box. This occurs regardless of transport method (iperf, samba, vsftpd).

Setup:
Desktop PC Win7 - Core i7 - 8 GB RAM
Dual NIC on mobo (realtek based) - Both NICs show as 1.0GBps speed when looking at their properties. So cabling is OK

IP Address1: 192.168.2.5
IP Address2: 192.168.3.5


Server:
Description:    Ubuntu 11.04
Linux NAS 2.6.38-11-server #50-Ubuntu SMP Mon Sep 12 21:34:27 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Core i5 2500 - 8 GB RAM
NICs are both intel GBit standalone cards:
> eth1      Link encap:Ethernet  HWaddr 00:1b:21:c8:37:b8  
          inet addr:192.168.2.24  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fec8:37b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26032587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21816404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33911116611 (33.9 GB)  TX bytes:16769168583 (16.7 GB)
          Interrupt:16 Memory:fbec0000-fbee0000 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:c7:5f:cb  
          inet addr:192.168.3.24  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fec7:5fcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:954211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:468194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1336546102 (1.3 GB)  TX bytes:25629837 (25.6 MB)
          Interrupt:18 Memory:fbac0000-fbae0000 

root@NAS:~# ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbag
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes

root@NAS:~# ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbag
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes


Test Case 1:
iperf with Win7 as client. As you can see, 1 side is full speed. Other side is 50%
> H:\>iperf -c 192.168.2.24 -fM -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 0.01 MByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.2.24, TCP port 5001
TCP window size: 0.01 MByte (default)
------------------------------------------------------------
[172] local 192.168.2.5 port 49512 connected with 192.168.2.24 port 5001
[ ID] Interval       Transfer     Bandwidth
**[172]  0.0-10.0 sec   474 MBytes  47.4 MBytes/sec**
[136] local 192.168.2.5 port 5001 connected with 192.168.2.24 port 35003
[ ID] Interval       Transfer     Bandwidth
[136]  0.0-10.0 sec  1005 MBytes   100 MBytes/sec

H:\>iperf -c 192.168._3_.24 -fM -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 0.01 MByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.3.24, TCP port 5001
TCP window size: 0.01 MByte (default)
------------------------------------------------------------
[172] local 192.168.3.5 port 49537 connected with 192.168.3.24 port 5001
[ ID] Interval       Transfer     Bandwidth
**[172]  0.0-10.0 sec   578 MBytes  57.7 MBytes/sec**
[136] local 192.168.3.5 port 5001 connected with 192.168.3.24 port 57831
[ ID] Interval       Transfer     Bandwidth
[136]  0.0-10.0 sec   941 MBytes  94.1 MBytes/sec


So sending to either cards (the Intel ones) I get the same slow upload speed Win7 -> Ubuntu.


Samba Test:
Sending 1.78GB from Win7 --> ubuntu. The speed is steady at ~ 16MB/s.....ie 1/8 of maxing GBit...
> root@NAS:~# ifstat 1
       eth0                eth2                eth1       
 KB/s in  KB/s out   KB/s in  KB/s out   KB/s in  KB/s out
    0.00      0.00      0.00      0.00  16354.30    239.99
    0.00      0.00      0.00      0.00  16353.96    238.34
    0.00      0.00      0.00      0.00  12986.69    205.09
    0.00      0.00      0.00      0.00  15604.02    234.73
    0.00      0.00      0.00      0.00  18083.86    321.21
    0.00      0.00      0.00      0.00  16767.73    249.29
    0.00      0.00      0.00      0.00  13696.14    215.18
    0.00      0.00      0.00      0.00  16846.52    253.00
    0.00      0.00      0.00      0.00  15993.81    235.11
    0.00      0.00      0.00      0.00  15290.37    234.01
    0.00      0.00      0.00      0.00  16620.51    263.51
    0.00      0.00      0.00      0.00  16088.49    251.59
    0.00      0.00      0.12      0.00  13429.76    196.31
    0.00      0.00      0.00      0.00  15955.56    239.92

Downloading the same files that i uploaded (ubuntu -> win7). I get steady full speed
>     0.00      0.00      0.00      0.00    706.87  94718.03
    0.00      0.00      0.00      0.00    881.64  119666.6
    0.00      0.00      0.12      0.00    826.10  118358.0
    0.00      0.00      0.00      0.00    799.14  120378.0
    0.00      0.00      0.00      0.00    798.54  120410.4
    0.00      0.00      0.00      0.00    799.01  120410.5
    0.00      0.00      0.00      0.00    799.77  120442.8
    0.00      0.00      0.00      0.00    797.67  120343.9
    0.00      0.00      0.12      0.12    542.68  81814.18
    0.00      0.00      0.00      0.00    316.51  42721.38
    0.00      0.00      0.00      0.00    881.03  119366.7
    0.00      0.00      0.00      0.00    820.03  117505.0
    0.00      0.00      0.00      0.00    799.07  120410.5
    0.00      0.00      0.16      0.16    798.72  120410.6


One thing to note is when I transfer either way. Iowait/CPU, etc are very low. Near 0. No system bottleneck.

VSFTPD Case:
> [Local -> vsftp 2.24] part1.rar 405.0 Mbytes/22.98(s)/18,475.88Kbps
[vsftp 2.24 -> Local] part1.rar 405.0 Mbytes/4.39(s)/96,714.48Kbps



So, it appears the issue is not application based since the same behavior occurs across vsftp and samba. Iperf gives me higher results than both applications....but still 50% of maxing the link


Anyone with ideas to make it max out both ways?

Ultimately, id like to bind both interfaces and make it look like a 2GB/s link...but first I need to figure out this basic issue.

One thing to take into consideration is that I have VMWare Server installed on the Ubuntu box.

---

