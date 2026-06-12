---
title: "dell inspiron 8200"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by iaw4 on 2009-07-29
I have a DELL Inspiron notebook, on which I just installed the latest ubuntu.  (it has a much higher res display than even the latest notebooks.)

the good news is that the wireless choices (top bar icon on the right) shows the available networks to choose from.  the networks that I want to connect to is currently wide open---no encryption or mac filtering.  my wireless access point even shows me that it assigned a DHCP entry to this dell computer.

the bad news is that no packages are ever received/sent by the notebook.  the ubuntu icon circles for a while, then it tells me that I am disconnected.

output from lspci -vv does not seem to contain "wireless" or "broadcom".

output from iwconfig and ifconfig are



lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"iaw4"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 06:24:01:45:22:F5   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:03:00:55  
          inet addr:192.168.0.163  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe03:55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:887007 (887.0 KB)  TX bytes:184297 (184.2 KB)
          Interrupt:11 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:57:9e:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2146 (2.1 KB)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


is this a known problem?  hints appreciated.

sincerely,

/iaw4

---

