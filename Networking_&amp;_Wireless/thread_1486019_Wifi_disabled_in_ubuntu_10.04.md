---
title: "Wifi disabled in ubuntu 10.04"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by Bhavneet on 2010-05-17
Hey everyone... m new to this forum... here's my 1st problem with ubuntu 10.04 :)...

the wireless is disabled... m using the Netgear WG111V3 usb adapter.... there was no problem in 9.10.. just plugged it in and the wireless was on... please help!

---

### Post by NUboon2Age on 2010-05-17
I suggest starting with providing the info requested in: [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by Bhavneet on 2010-06-05
Output of IFCONFIG:

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:f8:db:d8  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef8:dbd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1187531 (1.1 MB)  TX bytes:191441 (191.4 KB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:d1:44:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

OUTPUT OF IWCONFIG :
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

