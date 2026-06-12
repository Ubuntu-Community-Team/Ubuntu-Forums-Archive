---
title: "classmate and wifi, any scuccess?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by hilaire on 2009-11-21
Hello,

With a Classmate (CM2) installed with ubuntu 9.10, I've got a few problem.
Connection to the access point went nicely (attributed IP and DHCP information went to the laptop), but when I am trying to connect to the network the connection stalls.

Does anyone got similar experience?


See hardware and setup information:

```

wlan0     IEEE 802.11bg  ESSID:"olpc"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:5B:09:D5:8D   
          Bit Rate=48 Mb/s   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

teo@plume:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1d:92:cf:e6:74  
          inet adr:192.168.0.14  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::21d:92ff:fecf:e674/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:731 erreurs:0 :0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:192994 (192.9 KB) Octets transmis:19716 (19.7 KB)

teo@plume:~$ lsusb 
Bus 001 Device 002: ID 0ac8:c312 Z-Star Microelectronics Corp. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573


```

---

