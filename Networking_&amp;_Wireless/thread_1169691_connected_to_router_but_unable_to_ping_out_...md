---
title: "connected to router but unable to ping out .."
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by GreenSmurf on 2009-05-25
Hello all , 
 
I posted this thread 2 weeks ago : [http://ubuntuforums.org/showthread.php?t=1156046](http://ubuntuforums.org/showthread.php?t=1156046)
 
Since then , i was able to connect to other network , But i just can't connect to my own router . 
I told a friend of mine about my problem . He's working with ubuntu for along time now . I don't know exactly what he did . I know he install ndiswarpper and new driver for my wireless . 
Now , i have the wlan0 interface , and i'm able to use iwlist to scan wireless network (until now , iwlist show that none of my interfaces are not able to preform scanning . 
I have to say that my router is using mac address blocking and wep . But even when i remove all that , i'm unable to ping to my router (or anything else ) , even though i am connected . 
I'm posting all the necessary files (i think .. :))
 
ifconfig
 
eth0 Link encap:Ethernet HWaddr 00:21:70:86:6d:43 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:22 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:2070 (2.0 KB) TX bytes:2070 (2.0 KB)
wlan0 Link encap:Ethernet HWaddr 00:23:4d:70:9b:f8 
inet addr:192.168.2.126 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::223:4dff:fe70:9bf8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:6082 (6.0 KB)
Interrupt:17 Memory:f8000000-f8004000 
 
 
iwconfig
wlan0 IEEE 802.11g ESSID:"FuckOff" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:1F:1F:0B:4B:0F 
Bit Rate=54 Mb/s Tx-Power:32 dBm 
RTS thr:2347 B Fragment thr:2346 B 
Encryption key:8CD9-1D28-E60B-ACD7-BAB5-0C25-29 Security mode open
Power Management off
Link Quality:87/100 Signal level:-40 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:14 Invalid misc:49604 Missed beacon:0
&#12288;
 
iwlist_scanning (yes , my ssid if FuckOff .. I have stupid neighbor)
 
wlan0 Scan completed :
Cell 01 - Address: 00:1F:1F:0B:4B:0F
ESSID:"FuckOff"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:89/100 Signal level:-39 dBm Noise level:-96 dBm
Encryption key on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
 
lshw
*-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wlan0
version: 01
serial: 00:23:4d:70:9b:f8
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,09/20/2007, 4.170. ip=192.168.2.126 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
 
 
route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 * 255.255.255.0 U 2 0 0 wlan0
link-local * 255.255.0.0 U 1000 0 0 wlan0
default 192.168.2.1 0.0.0.0 UG 0 0 0 wlan0
&#12288;
ping - no surprise here .. ;)
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.126 icmp_seq=1 Destination Host Unreachable
From 192.168.2.126 icmp_seq=2 Destination Host Unreachable
From 192.168.2.126 icmp_seq=3 Destination Host Unreachable
From 192.168.2.126 icmp_seq=4 Destination Host Unreachable
From 192.168.2.126 icmp_seq=5 Destination Host Unreachable
--- 192.168.2.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4022ms
 
iptables
Chain INPUT (policy ACCEPT)
target prot opt source destination 
Chain FORWARD (policy ACCEPT)
target prot opt source destination 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
&#12288;
&#12288;
70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.
# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:70:86:6d:43", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:4d:70:9b:f8", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x4315 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:4d:70:9b:f8", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by kevdog on 2009-05-25
Honestly I wouldnt recommend using ndiswrapper.  There is a link about the Broadcom chipset reference in my signature.  Go there a figure out what driver to use -- I'm not certain if it b43 or the STA-wl module.  Either way I'd first go in that direction.

---

