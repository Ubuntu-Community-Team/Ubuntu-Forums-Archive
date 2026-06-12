---
title: "Help install multiple NICs, please?"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by tenmoi on 2009-03-19
First, I am sorry for asking on the wrong forum but Debian and Ubuntu are more or less brothers so I hope you'll not mind.

My debian lenny 64 recognizes two NICs: one integrated and one discrete but it wont recognize a third one.(both of the two discrete are from 3Com and in good condition)

the problem is that I am trying to attach each of my two Virtualbox machines to one NIC. And only the host and one of the two can go to the Internet. THe other virtual machine cannot because one of the physical discrete card (eth2_rename) is not working.

Here's the lspci:
 > 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:08.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

and strangely the result of ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:1a:4d:62:79:66  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe62:7966/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1886041 (1.7 MiB)  TX bytes:606265 (592.0 KiB)
          Interrupt:254 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:50:04:d9:0a:c4  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fed9:ac4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:770 errors:0 dropped:0 overruns:706 frame:0
          TX packets:530 errors:28 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111906 (109.2 KiB)  TX bytes:67877 (66.2 KiB)
          Interrupt:17 

eth2_rename Link encap:Ethernet  HWaddr 00:90:27:cf:0a:a0  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fecf:aa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2556057 (2.4 MiB)  TX bytes:171722 (167.6 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:958 (958.0 B)  TX bytes:958 (958.0 B)

eth0 is my onboard NIC


At first there was no eth2_rename because debian didnt recognize the third NIC. I manually inserted eth2 into the interfaces file and after that ifconfig gave me that name and the result above. (Note I manualy added the ip address.)

so thank you in advance.

P.S my board is Gigabyte ga m61p-sp3

---

