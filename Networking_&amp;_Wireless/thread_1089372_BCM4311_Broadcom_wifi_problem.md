---
title: "BCM4311 Broadcom wifi problem"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by miggerish on 2009-03-07
Hi,

I am new to this forum and new to ubuntu.  i have a laptop that recently had windows on it, but windows got wiped off and i had ubuntu reinstalled by a friend.  so now my wireless card is not working.  i am new to this so i would like some advice please.  i believe that it has to do with the driver for the wireless card.

thanks in advance.

---

### Post by labinnsw on 2009-03-07
Do you have Install Network Manager 0.7 SVN installed. If so your wireless should already be installed and just require configuring.

See this link [http://ubuntuforums.org/showthread.php?t=797059]("http://ubuntuforums.org/showthread.php?t=797059")

---

### Post by ugm6hr on 2009-03-07
We need more detail.  See the Wifi help link below.

---

### Post by miggerish on 2009-03-07
Okay, here are some important things i put into my command line thingy:

ubuntu@Ubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
ubuntu@Ubuntu:~$ /etc/apt/sources.list: deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
bash: /etc/apt/sources.list:: No such file or directory
ubuntu@Ubuntu:~$ deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
bash: deb: command not found
ubuntu@Ubuntu:~$ /etc/apt/sources.list deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
bash: /etc/apt/sources.list: Permission denied
ubuntu@Ubuntu:~$ 
ubuntu@Ubuntu:~$ 
ubuntu@Ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
ubuntu@Ubuntu:~$ lsusb
Bus 002 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:00cb Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@Ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:cf:ed:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:c5:ff:e3:25:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:14:68:49  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe14:6849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:220382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:296940881 (296.9 MB)  TX bytes:12680779 (12.6 MB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

ubuntu@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
ubuntu@Ubuntu:~$ ping 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
64 bytes from 208.67.219.101: icmp_seq=1 ttl=54 time=20.7 ms
64 bytes from 208.67.219.101: icmp_seq=2 ttl=54 time=18.4 ms
64 bytes from 208.67.219.101: icmp_seq=3 ttl=54 time=19.3 ms
ping64 bytes from 208.67.219.101: icmp_seq=4 ttl=54 time=19.5 ms
 64 bytes from 208.67.219.101: icmp_seq=5 ttl=54 time=17.8 ms
ww64 bytes from 208.67.219.101: icmp_seq=6 ttl=54 time=16.9 ms
w64 bytes from 208.67.219.101: icmp_seq=7 ttl=54 time=16.2 ms
64 bytes from 208.67.219.101: icmp_seq=8 ttl=54 time=16.0 ms
64 bytes from 208.67.219.101: icmp_seq=9 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=10 ttl=54 time=16.4 ms
64 bytes from 208.67.219.101: icmp_seq=11 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=12 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=13 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=14 ttl=54 time=17.7 ms
64 bytes from 208.67.219.101: icmp_seq=15 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=16 ttl=54 time=21.0 ms
64 bytes from 208.67.219.101: icmp_seq=17 ttl=54 time=19.5 ms
64 bytes from 208.67.219.101: icmp_seq=18 ttl=54 time=17.7 ms
64 bytes from 208.67.219.101: icmp_seq=19 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=20 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=21 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=22 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=23 ttl=54 time=17.7 ms
64 bytes from 208.67.219.101: icmp_seq=24 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=25 ttl=54 time=17.2 ms
64 bytes from 208.67.219.101: icmp_seq=26 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=27 ttl=54 time=24.7 ms
64 bytes from 208.67.219.101: icmp_seq=28 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=29 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=30 ttl=54 time=18.7 ms
64 bytes from 208.67.219.101: icmp_seq=31 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=32 ttl=54 time=17.1 ms
64 bytes from 208.67.219.101: icmp_seq=33 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=34 ttl=54 time=19.5 ms
64 bytes from 208.67.219.101: icmp_seq=35 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=36 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=37 ttl=54 time=17.1 ms
64 bytes from 208.67.219.101: icmp_seq=38 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=39 ttl=54 time=19.5 ms
64 bytes from 208.67.219.101: icmp_seq=40 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=41 ttl=54 time=16.0 ms
64 bytes from 208.67.219.101: icmp_seq=42 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=43 ttl=54 time=17.4 ms
64 bytes from 208.67.219.101: icmp_seq=44 ttl=54 time=16.6 ms
64 bytes from 208.67.219.101: icmp_seq=45 ttl=54 time=16.0 ms
64 bytes from 208.67.219.101: icmp_seq=46 ttl=54 time=19.3 ms
64 bytes from 208.67.219.101: icmp_seq=47 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=48 ttl=54 time=17.7 ms
64 bytes from 208.67.219.101: icmp_seq=49 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=50 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=51 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=52 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=53 ttl=54 time=21.0 ms
64 bytes from 208.67.219.101: icmp_seq=54 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=55 ttl=54 time=20.0 ms
64 bytes from 208.67.219.101: icmp_seq=56 ttl=54 time=21.5 ms
64 bytes from 208.67.219.101: icmp_seq=57 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=58 ttl=54 time=20.8 ms
64 bytes from 208.67.219.101: icmp_seq=59 ttl=54 time=20.9 ms
64 bytes from 208.67.219.101: icmp_seq=60 ttl=54 time=19.9 ms
64 bytes from 208.67.219.101: icmp_seq=61 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=62 ttl=54 time=18.4 ms
64 bytes from 208.67.219.101: icmp_seq=63 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=64 ttl=54 time=19.6 ms
64 bytes from 208.67.219.101: icmp_seq=65 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=66 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=67 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=68 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=69 ttl=54 time=16.9 ms
64 bytes from 208.67.219.101: icmp_seq=70 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=71 ttl=54 time=17.2 ms
64 bytes from 208.67.219.101: icmp_seq=72 ttl=54 time=16.5 ms
64 bytes from 208.67.219.101: icmp_seq=73 ttl=54 time=21.7 ms
64 bytes from 208.67.219.101: icmp_seq=74 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=75 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=76 ttl=54 time=16.4 ms
64 bytes from 208.67.219.101: icmp_seq=77 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=78 ttl=54 time=18.1 ms
64 bytes from 208.67.219.101: icmp_seq=79 ttl=54 time=17.1 ms
64 bytes from 208.67.219.101: icmp_seq=80 ttl=54 time=16.3 ms
64 bytes from 208.67.219.101: icmp_seq=81 ttl=54 time=18.1 ms
64 bytes from 208.67.219.101: icmp_seq=82 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=83 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=84 ttl=54 time=19.2 ms
64 bytes from 208.67.219.101: icmp_seq=85 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=86 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=87 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=88 ttl=54 time=16.2 ms
64 bytes from 208.67.219.101: icmp_seq=89 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=90 ttl=54 time=24.1 ms
64 bytes from 208.67.219.101: icmp_seq=91 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=92 ttl=54 time=19.2 ms
64 bytes from 208.67.219.101: icmp_seq=93 ttl=54 time=16.6 ms
64 bytes from 208.67.219.101: icmp_seq=94 ttl=54 time=18.4 ms
64 bytes from 208.67.219.101: icmp_seq=95 ttl=54 time=21.1 ms
64 bytes from 208.67.219.101: icmp_seq=96 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=97 ttl=54 time=21.7 ms
64 bytes from 208.67.219.101: icmp_seq=98 ttl=54 time=18.7 ms
64 bytes from 208.67.219.101: icmp_seq=99 ttl=54 time=19.6 ms
64 bytes from 208.67.219.101: icmp_seq=100 ttl=54 time=19.2 ms
64 bytes from 208.67.219.101: icmp_seq=101 ttl=54 time=22.4 ms
64 bytes from 208.67.219.101: icmp_seq=102 ttl=54 time=21.6 ms
64 bytes from 208.67.219.101: icmp_seq=103 ttl=54 time=17.0 ms
64 bytes from 208.67.219.101: icmp_seq=104 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=105 ttl=54 time=17.4 ms
64 bytes from 208.67.219.101: icmp_seq=106 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=107 ttl=54 time=19.9 ms
64 bytes from 208.67.219.101: icmp_seq=108 ttl=54 time=17.2 ms
64 bytes from 208.67.219.101: icmp_seq=109 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=110 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=111 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=112 ttl=54 time=19.2 ms
64 bytes from 208.67.219.101: icmp_seq=113 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=114 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=115 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=116 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=117 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=118 ttl=54 time=19.5 ms
64 bytes from 208.67.219.101: icmp_seq=119 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=120 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=121 ttl=54 time=19.3 ms
64 bytes from 208.67.219.101: icmp_seq=122 ttl=54 time=20.4 ms
64 bytes from 208.67.219.101: icmp_seq=123 ttl=54 time=17.6 ms
64 bytes from 208.67.219.101: icmp_seq=124 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=125 ttl=54 time=16.1 ms
64 bytes from 208.67.219.101: icmp_seq=126 ttl=54 time=17.5 ms
64 bytes from 208.67.219.101: icmp_seq=127 ttl=54 time=20.6 ms
64 bytes from 208.67.219.101: icmp_seq=128 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=129 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=130 ttl=54 time=16.3 ms
64 bytes from 208.67.219.101: icmp_seq=131 ttl=54 time=17.6 ms
64 bytes from 208.67.219.101: icmp_seq=132 ttl=54 time=20.0 ms
64 bytes from 208.67.219.101: icmp_seq=133 ttl=54 time=16.2 ms
64 bytes from 208.67.219.101: icmp_seq=134 ttl=54 time=17.4 ms
64 bytes from 208.67.219.101: icmp_seq=135 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=136 ttl=54 time=16.0 ms
64 bytes from 208.67.219.101: icmp_seq=137 ttl=54 time=20.4 ms
64 bytes from 208.67.219.101: icmp_seq=138 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=139 ttl=54 time=19.7 ms
64 bytes from 208.67.219.101: icmp_seq=140 ttl=54 time=16.9 ms
64 bytes from 208.67.219.101: icmp_seq=141 ttl=54 time=16.1 ms
64 bytes from 208.67.219.101: icmp_seq=142 ttl=54 time=23.3 ms
64 bytes from 208.67.219.101: icmp_seq=143 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=144 ttl=54 time=17.8 ms
64 bytes from 208.67.219.101: icmp_seq=145 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=146 ttl=54 time=19.3 ms
64 bytes from 208.67.219.101: icmp_seq=147 ttl=54 time=25.3 ms
64 bytes from 208.67.219.101: icmp_seq=148 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=149 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=150 ttl=54 time=17.3 ms
64 bytes from 208.67.219.101: icmp_seq=151 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=152 ttl=54 time=16.7 ms
64 bytes from 208.67.219.101: icmp_seq=153 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=154 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=155 ttl=54 time=18.1 ms
64 bytes from 208.67.219.101: icmp_seq=156 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=157 ttl=54 time=18.0 ms
64 bytes from 208.67.219.101: icmp_seq=158 ttl=54 time=19.8 ms
64 bytes from 208.67.219.101: icmp_seq=159 ttl=54 time=19.3 ms
64 bytes from 208.67.219.101: icmp_seq=160 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=161 ttl=54 time=18.9 ms
64 bytes from 208.67.219.101: icmp_seq=162 ttl=54 time=19.1 ms
64 bytes from 208.67.219.101: icmp_seq=163 ttl=54 time=19.4 ms
64 bytes from 208.67.219.101: icmp_seq=164 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=165 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=166 ttl=54 time=21.0 ms
64 bytes from 208.67.219.101: icmp_seq=167 ttl=54 time=348 ms
64 bytes from 208.67.219.101: icmp_seq=168 ttl=54 time=549 ms
64 bytes from 208.67.219.101: icmp_seq=169 ttl=54 time=668 ms
64 bytes from 208.67.219.101: icmp_seq=170 ttl=54 time=778 ms
64 bytes from 208.67.219.101: icmp_seq=171 ttl=54 time=861 ms
64 bytes from 208.67.219.101: icmp_seq=172 ttl=54 time=937 ms
64 bytes from 208.67.219.101: icmp_seq=173 ttl=54 time=1007 ms
64 bytes from 208.67.219.101: icmp_seq=174 ttl=54 time=1104 ms
64 bytes from 208.67.219.101: icmp_seq=175 ttl=54 time=1184 ms
64 bytes from 208.67.219.101: icmp_seq=176 ttl=54 time=1221 ms
64 bytes from 208.67.219.101: icmp_seq=177 ttl=54 time=1268 ms
64 bytes from 208.67.219.101: icmp_seq=178 ttl=54 time=1334 ms
^A^A64 bytes from 208.67.219.101: icmp_seq=179 ttl=54 time=1396 ms
64 bytes from 208.67.219.101: icmp_seq=180 ttl=54 time=1438 ms
64 bytes from 208.67.219.101: icmp_seq=181 ttl=54 time=1480 ms
64 bytes from 208.67.219.101: icmp_seq=182 ttl=54 time=1533 ms
64 bytes from 208.67.219.101: icmp_seq=183 ttl=54 time=1589 ms
64 bytes from 208.67.219.101: icmp_seq=184 ttl=54 time=1641 ms
64 bytes from 208.67.219.101: icmp_seq=185 ttl=54 time=1731 ms
^A64 bytes from 208.67.219.101: icmp_seq=186 ttl=54 time=1777 ms
^A64 bytes from 208.67.219.101: icmp_seq=187 ttl=54 time=1825 ms
^A64 bytes from 208.67.219.101: icmp_seq=188 ttl=54 time=1840 ms
^A64 bytes from 208.67.219.101: icmp_seq=189 ttl=54 time=1881 ms
64 bytes from 208.67.219.101: icmp_seq=190 ttl=54 time=1299 ms
64 bytes from 208.67.219.101: icmp_seq=191 ttl=54 time=295 ms
64 bytes from 208.67.219.101: icmp_seq=192 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=193 ttl=54 time=18.7 ms
64 bytes from 208.67.219.101: icmp_seq=194 ttl=54 time=16.0 ms
64 bytes from 208.67.219.101: icmp_seq=195 ttl=54 time=19.2 ms
64 bytes from 208.67.219.101: icmp_seq=196 ttl=54 time=18.5 ms
64 bytes from 208.67.219.101: icmp_seq=197 ttl=54 time=17.9 ms
64 bytes from 208.67.219.101: icmp_seq=198 ttl=54 time=19.0 ms
64 bytes from 208.67.219.101: icmp_seq=199 ttl=54 time=18.2 ms
64 bytes from 208.67.219.101: icmp_seq=200 ttl=54 time=16.3 ms
64 bytes from 208.67.219.101: icmp_seq=201 ttl=54 time=18.7 ms
64 bytes from


Also, here is more info.

I am trying to get online using my built in wireless hardware thingy on my HP laptop.  I have an AMD Turion64 X2 proccessor.  I do not have a dual boot with windows.  This computer has no windows on it, just ubuntu.  I am currently connected using the direct wire from my internet box thingy and conecting to my actual computer, physically.  I think this is called Ethernet.  If i place my cursor over the icon on my top right of the screen, where it says "wired network conection", and if i click it, it has th  word "wireless networks" in grey color text, and will not allow me to click it.

EDIT:  I have connected to the internet using the wireless on this laptop before, when I had windows installed as well as Ubuntu.

---

### Post by miggerish on 2009-03-07
Also, when I stopped the "ping" thing, it said this:

```

64 bytes from 208.67.219.101: icmp_seq=1099 ttl=54 time=19.6 ms
64 bytes from 208.67.219.101: icmp_seq=1100 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=1101 ttl=54 time=18.4 ms
64 bytes from 208.67.219.101: icmp_seq=1102 ttl=54 time=17.3 ms
64 bytes from 208.67.219.101: icmp_seq=1103 ttl=54 time=18.6 ms
64 bytes from 208.67.219.101: icmp_seq=1104 ttl=54 time=18.8 ms
64 bytes from 208.67.219.101: icmp_seq=1105 ttl=54 time=17.0 ms
64 bytes from 208.67.219.101: icmp_seq=1106 ttl=54 time=18.3 ms
64 bytes from 208.67.219.101: icmp_seq=1107 ttl=54 time=18.6 ms
^C
--- 208.67.219.101 ping statistics ---
1107 packets transmitted, 1107 received, 0% packet loss, time 1111268ms
rtt min/avg/max/mdev = 15.923/108.622/2038.297/328.335 ms, pipe 3
ubuntu@Ubuntu:~$ 



```

---

### Post by ugm6hr on 2009-03-07
What version of Ubuntu are you using?

This is the most important bit:
```
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

The BCM4311 is supported by the new b43 driver.

Go to System -. Administration -> Hardware drivers and ensure it is enabled.

I will change the thread title to something more useful for you.

EDIT: You can try searching for help using BCM4311 or Broadcom as terms.

---

### Post by miggerish on 2009-03-07
> **ugm6hr said:**
> What version of Ubuntu are you using?

This is the most important bit:
```
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

The BCM4311 is supported by the new b43 driver.

Go to System -. Administration -> Hardware drivers and ensure it is enabled.

I will change the thread title to something more useful for you.

EDIT: You can try searching for help using BCM4311 or Broadcom as terms.

I am using version 8.10

---

### Post by miggerish on 2009-03-07
Thanks, it worked!  I Just had to activate the driver like you said.  My problem is solved.

---

