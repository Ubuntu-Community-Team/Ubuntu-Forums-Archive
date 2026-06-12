---
title: "Billions of packets even when cable not connected, cannot disable eth0"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by chosenperfect on 2011-05-13
root@f:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:78:22  
          inet addr:192.168.10.31  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:597043403678532 errors:3582286191871471 dropped:1194095397290490 overruns:597047698645245 frame:2985238493226226
          TX packets:597047698645352 errors:2388190794580980 dropped:0 overruns:597047698645245 carrier:1194095397290492
          collisions:2985238493226225 txqueuelen:1000 
          RX bytes:597047698691310 (597.0 TB)  TX bytes:597047698661043 (597.0 TB)
          Interrupt:46 

### 2 minutes later


eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:78:22  
          inet addr:192.168.10.31  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:615224000238267 errors:3691369771229881 dropped:1230456590409960 overruns:615228295204980 frame:3076141476024901
          TX packets:615228295205087 errors:2460913180819920 dropped:0 overruns:615228295204980 carrier:1230456590409962
          collisions:3076141476024900 txqueuelen:1000 
          RX bytes:615228295251045 (615.2 TB)  TX bytes:615228295220778 (615.2 TB)
          Interrupt:46 


### after sudo ifconfig eth0 down



eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:78:22  
          inet addr:192.168.10.31  Bcast:192.168.10.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:620597004324312 errors:3723607795746151 dropped:1241202598582050 overruns:620601299291025 frame:3103006496455126
          TX packets:620601299291132 errors:2482405197164100 dropped:0 overruns:620601299291025 carrier:1241202598582052
          collisions:3103006496455125 txqueuelen:1000 
          RX bytes:620601299337090 (620.6 TB)  TX bytes:620601299306823 (620.6 TB)
          Interrupt:46 


# using ubuntu 11.04, anyone know why this happened?
# after restarting my laptop, everything seems working fine
# but it was happening again sometime after disconnecting a cable/ disable "Enable Networking" on Network Manager..
# thanks in advance

---

