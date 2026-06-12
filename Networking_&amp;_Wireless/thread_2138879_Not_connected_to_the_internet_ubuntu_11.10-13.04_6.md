---
title: "Not connected to the internet ubuntu 11.10-13.04 64bit"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by crywolf1987 on 2013-04-25
ust want to apologize for my bad English. I have a motherboard ASRock N68-VS3 FH. And when installing or starting with a live disk ubuntu 11.04-13.04 does not work online. Ie if only he tries to connect but DHTSP not receiving data. If you manually set the data bit as connected but still no internet. Climb on the internet found that this bug [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) source / linux / bug/1003297 and below as I read it with 64bit and owned with this motherboard

(SourcePackage: linux
 UpgradeStatus: No upgrade log present (probably fresh install)
 dmi.bios.date: 10/07/2011
 dmi.bios.vendor: American Megatrends Inc.
 dmi.bios.version: P1.20
 dmi.board.name: N68-VS3 FX
 dmi.board.vendor: ASRock
 dmi.chassis.asset.tag: To Be Filled By O.E.M.
 dmi.chassis.type: 3
 dmi.chassis.vendor: To Be Filled By O.E.M.
 dmi.chassis.version: To Be Filled By O.E.M.
 dmi.modalias: dmi:bvnAmericanMegatrendsInc.:bvrP1.20:bd10/07/2011:svnToBeFilledByO.E.M.:pnToBeFilledByO.E.M.:pvrToBeFilledByO.E.M.:rvnASRock:rnN68-VS3FX:rvr:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:
 dmi.product.name: To Be Filled By O.E.M.
 dmi.product.version: To Be Filled By O.E.M.
 dmi.sys.vendor: To Be Filled By O.E.M.)

However, if you install the 32bit then the internet works. How can I solve this problem and make the Internet work on 64bit?

**lshw -C network **
```
*-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 00
       serial: 00:4f:6a:04:a4:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.5.0-17-generic firmware=0.8 latency=32 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:febf8000-febfffff
```

lspci | awk '/[nN]et/{print $1}' | xargs -i lspci -knns {}
```
ns {}
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
01:0a.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci
```

ip -s l 
```
lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN mode DEFAULT 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    RX: bytes  packets  errors  dropped overrun mcast   
    56344      698      0       0       0       0      
    TX: bytes  packets  errors  dropped carrier collsns 
    56344      698      0       0       0       0      
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT qlen 1000
    link/ether bc:5f:f4:06:fd:a6 brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast   
    0          0        29102   0       0       151    
    TX: bytes  packets  errors  dropped carrier collsns 
    40692      213      0       88      0       0      
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT qlen 1000
    link/ether 00:4f:6a:04:a4:3f brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast   
    0          0        0       0       0       0      
    TX: bytes  packets  errors  dropped carrier collsns 
    0          0        0       0       0       0
```

---

