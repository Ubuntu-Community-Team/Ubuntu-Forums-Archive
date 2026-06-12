---
title: "Network Slow! Windows to Ubuntu."
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by synpey on 2010-02-13
[FONT=Courier New]hi.

I'm using Ubuntu Server 8.04 on Dell inspiron 9 with usbhdd as samba file server.
I recently find file transfer from Windows to Ubuntu is slower than Ubuntu to Windows, and then performed some check.The results are as follow.

<M1> 
 OS:WinXP SP2 
 NIC:1Gbps
 <M2> 
 OS:Ubuntu Server 8.04 
  NIC:100Mbps
<Network>
M1-Router-M2

<netperf result>
Recv   Send    Send 
 Socket Socket  Message   Elapsed 
 Size   Size    Size     Time     Throughput 
 bytes   bytes   bytes    secs.    10^6bits/sec 
  
 M1 -> M2 
     256   8192   8192    10.00       7.86 
 Vitrtual WinXP@M1 -> M2 
     256   8192   8192    10.00       4.70 
 M2 -> M1 
   8192   16384  16384    10.01      93.69 
 Virtual WinXP@M1 -> M1 
   8192    8192   8192    10.00     142.00 
 Virtual Linux@M1 -> M2 
  87380   16384  16384    10.01      90.31 
 Virtual Win7RC@M1 -> M1 
   8192    8192   8192    10.00     168.23 
 Virtual Win7RC@M1 -> M2 
    256    8192   8192    10.00       2.79 

<ethtool on M2 result>[/FONT][FONT=Courier New]
 Settings for eth0: 
         Supported  ports: [ TP MII ] 
         Supported link modes:   10baseT/Half  10baseT/Full 
                                 100baseT/Half  100baseT/Full 
         Supports auto-negotiation: Yes 
          Advertised link modes:  100baseT/Full 
         Advertised  auto-negotiation: Yes 
         Speed: 100Mb/s 
         Duplex:  Full 
         Port: MII 
         PHYAD: 0 
          Transceiver: internal 
         Auto-negotiation: on 
          Supports Wake-on: pumbg 
         Wake-on: g 
         Current  message level: 0x00000033 (51) 
         Link detected: yes


Anyone has idea what's wrong?[/FONT]

---

