---
title: "Netgear wireless card problems ubuntu 10.10"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Albert3386 on 2011-01-05
I have set up ndiswrapper and configured all drivers for the card when i run if config i get this 
                     
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:e0:96:3e   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:23  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:108 errors:0 dropped:0 overruns:0 frame:0  
           collisions:0 txqueuelen:0  
           RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:8c:e9:fc   
           inet6 addr: fe80::20f:b5ff:fe8c:e9fc/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:16 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17 Memory:f6010000-f6020000          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0  
  
Then if i run iwconfig i get this 

wlan0     IEEE 802.11g  ESSID:"dlink"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:1A:C1:6C    
           Bit Rate=1 Mb/s   Sensitivity=-200 dBm   
           RTS thr=2346 B   Fragment thr=2346 B    
           Power Management:off  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 



Everything looks ok But when i come to connect through network manager which can see the router it asks for the wpa code. I enter the code and it tries to connect. It will ask me for the wpa code twice more then come up with the not connected message.


Any help would be appreciated.

---

