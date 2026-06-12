---
title: "3954ABG won't work on my Dell Inspiron 1720"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by nafihsus on 2009-06-06
I am getting somewhat frustrated as no one seems to have a similar problem. 3945ABG should work out of the box, but in my case it does not. I tried ndiswrapper as well but also failed (wlan on XP ran out of the box when I bought the system before replacing it with Ubuntu 8.04 (64bit).

The attached file contains all info related to the problem as described in the Wiki.

Hope someone can help.

1 ) Machine Brand and Model (PC/Laptop):
Laptop, Dell, Inspiron 1720

2 ) Wireless Brand, Model and Wireless Chipset:
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

$ lspci -nn | grep 'Intel'
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)


3 ) check interface:
command run with LAN connected!

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ce:e8:bd
          inet addr:192.168.2.99  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fece:e8bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3025696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3275240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1822630734 (1.6 GB)  TX bytes:2258927693 (2.1 GB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:107638 (105.1 KB)  TX bytes:107638 (105.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:1a:36:30
          inet addr:192.168.2.96  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe1a:3630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1264520 (1.2 MB)  TX bytes:12569359 (11.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-1A-36-30-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


4 ) Check for modules:
$ lsmod | grep 3945

iwl3945                96244  0
lbm_iwl_mac80211      242292  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211


5 ) Kernel boot messages
$ dmesg | grep 3945
[   26.556744] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   26.556748] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   26.556918] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   26.663540] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.699505] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   26.899046] input: 3945ABG as /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/input/input11
[   27.732813] iwl3945: Radio disabled by HW RF Kill switch
[   27.750225] iwl3945: Radio disabled by HW RF Kill switch
[   27.750790] iwl3945: Radio disabled by HW RF Kill switch
[   33.504175] iwl3945: Radio disabled by HW RF Kill switch
[   33.510114] iwl3945: Radio disabled by HW RF Kill switch
[   33.510674] iwl3945: Radio disabled by HW RF Kill switch
[   36.580534] iwl3945: Radio disabled by HW RF Kill switch

6 ) Network configuration
$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:1a:36:30
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.96 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ce:e8:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.99 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

7 ) Scan for networks:
$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:41:34:9A
                    ESSID:"eldewlan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=93/100  Signal level:-36 dBm  Noise level=-64 dBm
                    Encryption key:on
                    IE: Unknown: 2D1A4C1003FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000007a0cea7180
                    Extra:Last beacon:80ms ago


8 ) Ubuntu Version:
$ lsb_release -d
Description:    Ubuntu 8.04.2

9 ) Kernel/architecture (including 32 vs. 64 bit):
$ uname -mr
2.6.24-24-generic i686

10 ) Restarting the network:
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                               RTNETLINK answers: No such process

---

### Post by chili555 on 2009-06-06
> [ 36.580534] iwl3945: Radio disabled by HW RF Kill switchThere is a switch or key combination that turns your wireless on and off. It is off.

However, this looks quite good:> wlan0 Link encap:Ethernet HWaddr 00:1f:3c:1a:36:30
inet addr:192.168.2.96 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::21f:3cff:fe1a:3630/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6274 errors:0 dropped:0 overruns:0 frame:0
TX packets:13066 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1264520 (1.2 MB) TX bytes:12569359 (11.9 MB)Taken by itself, this looks like your wireless is working perfectly! What is the symptom that suggests it's not working?

---

### Post by nafihsus on 2009-06-06
I can't connect to any internet page, ping does not even reply when trying to reach the routoer.

---

### Post by nafihsus on 2009-06-07
Very strange! Since this morning the Wireless connection works and I did not change anything - the system wasn't even rebooted.

I later rebooted without the LAN being plugged in. It took around 2 minutes until the WLAN worked! I hope it stays stable. I'll post back in case it does not.

---

### Post by nafihsus on 2009-06-09
Today again no Wireless - but working on two other PCs!

Can someone please check this ifconfig and ping command. 192.168.2.99 ist the LAN interface .96 the WLAN. LAN was unplugged at boot and later on.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ce:e8:bd
          inet addr:192.168.2.99  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:72002 (70.3 KB)  TX bytes:72002 (70.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:1a:36:30
          inet addr:192.168.2.96  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe1a:3630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:420 (420.0 B)  TX bytes:4400 (4.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-1A-36-30-00-00-00-00-00-00-00-00-00                                -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cenk@cenk1:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.99 icmp_seq=1 Destination Host Unreachable
From 192.168.2.99 icmp_seq=2 Destination Host Unreachable
From 192.168.2.99 icmp_seq=3 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4016ms
, pipe 3

---

