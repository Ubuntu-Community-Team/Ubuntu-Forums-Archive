---
title: "Slow speed with wn111 and ubuntu"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Noggenfogger on 2009-02-18
Hi

I am using Netgear WNR834Bv2 wireless router along with a Netgear WN111 Wireless USB adapter.
Both are 802.11n compliant.

I have got the USB Wireless adapter up and running via ndiswrapper, but speed is low, about 11mbit max.
Using the same adapter in windows gives good speed.

I have no encryption method etc activated. Speed on router 270Mb/s. Works with windows. Doesn't matter if I set the speed on the router to lower modes (130, 54 etc), speed is the same.


One thing that bothers me is the output from lshw -C network (se below) that says "wireless=IEEE 802.11g", shouldn't it say 802.11n ? Can this be my problem? I can't find any info on this thought. Anyway, using 802.11g should give me more than 10Mb/s anyway right? 
Also: iwlist wlan0 modulation command gives:
wlan0     unknown modulation information.
Is this ok?

Is there anyone that have had this problem and can point me in the right direction so I can solve it?



troubleshooting info:

Ubuntu version: Intrepid 8.10 32bit, latest patches.


Using iwconfig wlan0 shows 270Mb/s:
wlan0     IEEE 802.11g  ESSID:"2slow4ever"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:2A:0B:C8:88
          Bit Rate=270 Mb/s   Sensitivity=-200 dBm
          RTS thr=2346 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

Ndiswrapper:
~$ ndiswrapper -l
netmw245 : driver installed
        device (0846:9000) present

Ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:ce:9d:2e
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fece:9d2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2359850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1449384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3119952563 (3.1 GB)  TX bytes:576261154 (576.2 MB)

  
lshw -C network:
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:ce:9d:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Netgear,11/19/2007,1.0.7.3 ip=192.168.1.8 link=yes multicast=yes wireless=IEEE 802.11g


wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:0B:C8:88
                    ESSID:"2slow4ever"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


$iwlist wlan0 modulation
wlan0     unknown modulation information.

---

### Post by Noggenfogger on 2009-02-20
anyone have any idea?

---

