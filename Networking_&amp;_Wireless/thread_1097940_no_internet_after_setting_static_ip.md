---
title: "no internet after setting static ip"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2009-03-16
I reset my IP address to a static IP 192.168.1.XXX in "system/Preferences/Network Configuration" making changes to the "wireless" tab by removing the autostat, and putting in the address that was found from "ifconfig" that is listed as "HWADDr 00:16:cf:0b:xx:xx" in the MAC address field, and then set up a static IP adress and put in the broadcast and gateway, and for the DNS I used the same address as the gateway.  I rebooted and it shows the new IP address, and I have to connect manualy to the network, but when I try and access the internet it goes nowhere?  I ran iwconfig and got the following before I made the change:
nitewalker@smj:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"08FX10081863"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:A6:61:C8   
          Bit Rate:48 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-33 dBm  Noise level=-92 dBm
          Rx invalid nwid:1163  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

nitewalker@smj:~$

and when I ran ifconfig before I made the change I got the following:

nitewalker@smj:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:0b:01:d2  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe0b:1d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1324265 (1.3 MB)  TX bytes:575484 (575.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:d4:14:9f:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-0B-01-D2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9066 errors:0 dropped:0 overruns:0 frame:510
          TX packets:2246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2180074 (2.1 MB)  TX bytes:677444 (677.4 KB)
          Interrupt:22 

nitewalker@smj:~$

any help appriciated.

---

