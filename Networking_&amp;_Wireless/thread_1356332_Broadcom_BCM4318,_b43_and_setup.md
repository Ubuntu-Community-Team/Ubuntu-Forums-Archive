---
title: "Broadcom BCM4318, b43 and setup"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by BCollar on 2009-12-15
Hello, I am new to Ubuntu and these forums.  Thank you in advance for your help.

I just installed Ubuntu 9.10 (single partition, single OS install) the computer is a Gateway MX7340. And I am trying to get my Broadcom BCM4318 wireless adapter installed and connected to the internet.  It is WPA2 protected and the SSID is not broadcasted.

I did a fresh re-stall, from disk with active LAN connection.  In the OS I used the "Hardware Drivers" utility and downloaded/activated the b43 driver with the internet connected.

lspci entry is: 

01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

ifconfig is: 

eth0      Link encap:Ethernet  HWaddr 00:03:25:2b:be:7e  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe2b:be7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5164733 (5.1 MB)  TX bytes:304595 (304.5 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:44:3a:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-44-3A-73-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig is: 

 IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Wait- I think I just made a breakthrough!  I was right-clicking over the internet connection task instead of left clicking..  I'm connected now! Also I think my adapter was off, I activated it through the FN antenna button action.

I hope this helps someone.

---

