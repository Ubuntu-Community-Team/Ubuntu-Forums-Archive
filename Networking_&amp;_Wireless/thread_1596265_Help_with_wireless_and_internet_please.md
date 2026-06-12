---
title: "Help with wireless and internet please"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by John McCarthy on 2010-10-14
Hello

It has been suggested i post code results for 
sudo lshw -C network  and iwconfig.   Please see below for results:  Any help greatly appreciated

kate@kate-laptop:~$ sudo lshw -C network
[sudo] password for kate:
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:13:2b:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.1.1.7 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:b6:52:25
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
kate@kate-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:227  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

kate@kate-laptop:~$

---

### Post by Buggrit on 2010-10-14
Great config file. 

We could probably help more if we knew what the actual problem you are experiencing is?

JB

---

### Post by dineshs on 2010-10-14
Can you also post the results of
```
route -n
```and```
ping 4.2.2.1 -c4
```

---

### Post by smilodonis on 2010-10-14
Im not expert at this but i guess there is no internet connection on that machine via wifi. 

If I do an iwconfig, i usually get a list where I can find my wifi card (named wlan0). At this point I can assume that you want to connect the internet using a wifi card. And that is missing from your iwconfig. If so, try to install/update your wifi drivers, or check if the card/USB (whatever) is plugged in or its working. Maybe even try it on some other computer if you can,.

---

### Post by John McCarthy on 2010-10-14
thanks all for your comments.

My appologies for not providing more detail on exactr problem.

Problem:  I have a wireless router (belkin) which i know is working OK since i can access internet via my work laptop which runs windows.   My wife has a dell mini 9 laptop, that was able to access our wireless system some 3-4 mths ago but we moved and now for her laptop it shows a connection to home network', but firefox cannot access internet, firefox said to check firewall, and i didnt seem to have firewall manager on the system so i was able to download the gufw firewall manager and latest ubuntu updates(which surprised me as i assume this must mean i actually can access the internet just cant access it via a browser ?) Since then i have played around with settings trying to fix by trial and error....obviously not best approach.

So in summary

I am sure i have wireless capability
Appears i can connect to home network Ok
Can download updates and software via synaptic manager. 

Thanks
John

---

### Post by John McCarthy on 2010-10-14
As requested

please find results for route -n    and    ping 4.2.2.1

I have also posted 
screenshot from my windows PC detailing the wireless connection properties (not sure if this is beneficial ?)




route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U     2      0        0 eth1
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth1


kate@kate-laptop:~$ ping 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=54 time=182 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=6 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=7 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=8 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=9 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=10 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=11 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=12 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=13 ttl=54 time=194 ms
64 bytes from 4.2.2.1: icmp_seq=14 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=15 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=16 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=17 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=18 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=19 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=20 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=21 ttl=54 time=169 ms
64 bytes from 4.2.2.1: icmp_seq=22 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=23 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=24 ttl=54 time=189 ms
64 bytes from 4.2.2.1: icmp_seq=25 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=26 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=27 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=28 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=29 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=30 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=31 ttl=54 time=171 ms

64 bytes from 4.2.2.1: icmp_seq=32 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=33 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=34 ttl=54 time=169 ms
64 bytes from 4.2.2.1: icmp_seq=35 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=36 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=37 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=38 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=39 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=40 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=41 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=42 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=43 ttl=54 time=169 ms
64 bytes from 4.2.2.1: icmp_seq=44 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=45 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=46 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=47 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=48 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=49 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=50 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=51 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=52 ttl=54 time=169 ms
64 bytes from 4.2.2.1: icmp_seq=53 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=54 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=55 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=56 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=57 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=58 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=59 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=60 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=61 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=62 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=63 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=64 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=65 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=66 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=67 ttl=54 time=250 ms
64 bytes from 4.2.2.1: icmp_seq=68 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=69 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=70 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=71 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=72 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=73 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=74 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=75 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=76 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=77 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=78 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=79 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=80 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=81 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=82 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=83 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=84 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=85 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=86 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=87 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=88 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=89 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=90 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=91 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=92 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=93 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=94 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=95 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=96 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=97 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=98 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=99 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=100 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=101 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=102 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=103 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=104 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=105 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=106 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=107 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=108 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=109 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=110 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=111 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=112 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=113 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=114 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=115 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=116 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=117 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=118 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=119 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=120 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=121 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=122 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=123 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=124 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=125 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=126 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=127 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=128 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=129 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=130 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=131 ttl=54 time=169 ms
64 bytes from 4.2.2.1: icmp_seq=132 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=133 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=134 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=135 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=136 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=137 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=138 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=139 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=140 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=141 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=142 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=143 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=144 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=145 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=146 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=147 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=148 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=149 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=150 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=151 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=152 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=153 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=154 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=155 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=156 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=157 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=158 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=159 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=160 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=161 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=162 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=163 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=164 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=165 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=166 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=167 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=168 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=169 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=170 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=171 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=172 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=173 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=174 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=175 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=176 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=177 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=178 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=179 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=180 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=181 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=182 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=183 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=184 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=185 ttl=54 time=174 ms
64 bytes from 4.2.2.1: icmp_seq=186 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=187 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=188 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=189 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=190 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=191 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=192 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=193 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=194 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=195 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=196 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=197 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=198 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=199 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=200 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=201 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=202 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=203 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=204 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=205 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=206 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=207 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=208 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=209 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=210 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=211 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=212 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=213 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=214 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=215 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=216 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=217 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=218 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=219 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=220 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=221 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=222 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=223 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=224 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=225 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=226 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=227 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=228 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=229 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=230 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=231 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=232 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=233 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=234 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=235 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=236 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=237 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=238 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=239 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=240 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=241 ttl=54 time=173 ms
64 bytes from 4.2.2.1: icmp_seq=242 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=243 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=244 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=245 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=246 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=247 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=248 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=249 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=250 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=251 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=252 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=253 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=254 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=255 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=256 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=257 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=258 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=259 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=260 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=261 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=262 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=263 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=264 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=265 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=266 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=267 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=268 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=269 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=270 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=271 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=272 ttl=54 time=172 ms
64 bytes from 4.2.2.1: icmp_seq=273 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=274 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=275 ttl=54 time=170 ms
64 bytes from 4.2.2.1: icmp_seq=276 ttl=54 time=171 ms
64 bytes from 4.2.2.1: icmp_seq=277 ttl=54 time=171 ms
^C
--- 4.2.2.1 ping statistics ---
277 packets transmitted, 277 received, 0% packet loss, time 276299ms
rtt min/avg/max/mdev = 169.237/172.018/250.572/5.168 ms
kate@kate-laptop:~$


Here are the details from the wireless connection taken off my windows laptop


Connection-specific DNS Suffix: 
Description: Intel(R) Wireless WiFi Link 4965AGN
Physical Address: 00-13-E8-86-97-8B
DHCP Enabled: Yes
IPv4 IP Address: 10.1.1.9
IPv4 Subnet Mask: 255.0.0.0
Lease Obtained: 12 October 2010 09:06
Lease Expires: 15 October 2010 09:28
IPv4 Default Gateway: 10.1.1.1
IPv4 DHCP Server: 10.1.1.1
IPv4 DNS Server: 10.1.1.1
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes
Link-local IPv6 Address: fe80::548d:1413:5fff:23e1%10
IPv6 Default Gateway: fe80::f88a:2876:9d1b:cccd%10
IPv6 DNS Server: fe80::f88a:2876:9d1b:cccd%10


thanks
John

---

### Post by John McCarthy on 2010-10-14
Hello all

here is the wireless properties details screenshot that i took from my windows laptop, hope it may help solve the problem. Ref attached

Cheers
John

---

### Post by John McCarthy on 2010-10-14
sorry all, i realise now i left off -c4 from my ping code (which obviously now i relise restricts the lines to 4 only)

---

### Post by dineshs on 2010-10-15
Please see if this works
Right-click on the NM icon( on top right of the panel) and then click on Edit Connections. 
Select the tab, wireless
select the  connection and click edit
select ipv4 
method-Automatic DHCP addresses only
Enter DNS as[COLOR="Blue"] 4.2.2.1[/COLOR]
then click apply 
Any progress?

---

### Post by nikalek on 2010-10-15
Hello,

Since I seem to be experiencing a very similar problem, I will add to this post. I am also on a wireless connection, which is not working as it should. I seem to be able to access some websites (this forum, for instance), but the browser (Firefox, although I also gave Epiphanyy a go) fails in opening most new sites, Firefox claiming "Problem loading page: The connection has timed out. The server at . . .  is taking too long to respond." Similarly, either browser was unable to stream audio or video content (Grooveshark or Youtube) more than a few seconds before buffering. I am able to access such content with my two other computers running Windows 7 and Windows XP. Ubuntu-updates and the software centre, however, seem to be working alright. Meanwhile, Firefox downloads, on occasion, fail to complete.

**Results for *sudo lshw -C network***
*-network:0             
       description: Ethernet interface
       product: 79c978 [HomePNA]
       vendor: Advanced Micro Devices [AMD]
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth1
       version: 52
       serial: 00:05:6e:00:36:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 latency=64 link=no maxlatency=24 mingnt=24 multicast=yes
       resources: irq:19 ioport:d400(size=32) memory:febffc00-febffc1f
  *-network:1
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 11
       serial: 00:11:09:86:0c:19
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:18 ioport:d000(size=256) memory:febff800-febff8ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:1a:4d:35:ad:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.33 link=yes multicast=yes wireless=IEEE 802.11bg

[B]Results for *iwconfig*
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"uchimura"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:CF:5F:83:C2   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**Results for *route -n***
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

[B]Results for [I]ping 4.2.2.1 -c4
[/I][/B]PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=245 time=54.7 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=245 time=50.8 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=245 time=52.6 ms
64 bytes from 4.2.2.1: icmp_req=4 ttl=245 time=51.4 ms

--- 4.2.2.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 50.891/52.440/54.747/1.486 ms


Any help is much appreciated. 
/Aleksi

---

### Post by nikalek on 2010-10-16
Oops, seems I posted this twice, aplogies. Took ages to load and I guess I went in and clicked the submit reply button more than once.

---

### Post by nikalek on 2010-10-16
Anyone?

I also cannot use any MSN-applications (tried aMSN, Emesene and Empathy). 

Feel free to embarass me with a ridiculously simple solution, I'll take it on the chin. :)

---

### Post by nikalek on 2010-10-16
Furthermore, I receive the following notification at start-up having established a connection:
[B]
Network service discovery disabled.
Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.[/B]

Again, any help would be much appreciated.
/Aleksi

---

### Post by ArgusVision on 2010-10-16
I installed 10.10 on a friend's Acer 4520 last Wednesday. I believe it has the same broadcom card and is having similar connectivity issues. It worked for a few hours, then strangely enough stopped. I think it may have to do with the interface being assigned as eth1 and not being seen as a wireless interface. When she went to System > Administration > Network Tools and Selected the eth1 interface it was listed as an ethernet interface (hardwire) instead of wireless. There's a post from back in 2007 that seems like it maybe interesting.
[http://ubuntuforums.org/archive/index.php/t-338332.html](http://ubuntuforums.org/archive/index.php/t-338332.html)
The intermittent name change experienced by this user could be similar to what we're experiencing. (Although that's purely conjecture at this point.)
I won't be able to get my hands on her PC again until tomorrow at the earliest. But could you post your /etc/network/interfaces file contents?
Thank's

---

### Post by ArgusVision on 2010-10-16
Forte125 left this as a tip in [http://ubuntuforums.org/showthread.php?t=1596043&highlight=broadcom+eth1](http://ubuntuforums.org/showthread.php?t=1596043&highlight=broadcom+eth1)


sudo rfkill unblock wifi

It seemed to work for that user (temporarily)
Could you try it and see if it does any good. I'm going to call the person I was helping and get her to try it. It seems to only be a temporary band-aid fix though.

---

### Post by ArgusVision on 2010-10-16
fyi, it didn't work for her. Still trying to figure out a fix other than reverting to 10.04.

---

### Post by nikalek on 2010-10-17
Hi,

thanks for your reply. I did my best to investigate as you instructed, but given my lack of experience with Linux, I am not yet too comfortable with the Terminal and its commands.

However, In System > Administration > Network Tools, the eth1 interface was, indeed, listed as ethernet interface.

Typed ```
sudo gedit /etc/network/interfaces
``` (I'm guessing the command used here is incorrect) with the following results:
[B]
auto lo
iface lo inet loopback[/B]

Finally, tried the ```
sudo rfkill unblock wifi
``` -code to no apparent results.

Much obliged,
Aleksi

---

