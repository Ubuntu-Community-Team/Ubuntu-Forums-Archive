---
title: "Help setting up wireless internet on ubuntu"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by lilchiko on 2009-04-09
Hello everyone. I am new to Ubuntu and I'm having problems getting my internet to work. When I go in the network manager I see my wireless network but I can't connect to it. I enter the ipconfig and iwconfig and this is what I got.



edward@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:15:c5:c8:d4:63 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:246 errors:0 dropped:0 overruns:0 frame:0
TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:15408 (15.4 KB) TX bytes:15408 (15.4 KB)

edward@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry min limit:7 RTS thrff Fragment thr=2352 B 
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

edward@ubuntu:~$ 


Please let me know if I am missing something. Thanks

---

