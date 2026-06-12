---
title: "can't share my wireless connexion"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by phoenixpb on 2010-12-07
I have a usb dongle for wireless works fine can connect to any rooter.

dnsmasq-base is installed
dnsmasq is not installed

when i create a new wireless connexion UbuntuAdhoc connexion try to connect during several mins and disconnect

phoenix@phoenix:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-mode ad-hoc
wireless-channel 4
wireless-essid 'phoenix'
wireless-key 1234567890
address 192.168.0.112
netmask 255.255.255.0
gateway 192.168.0.1

ethernet card connected to internet has 192.168.0.11 (gateway 192.168.0.1)

phoenix@phoenix:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:11:d8:bc:58:8f
inet addr:192.168.0.11 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::211:d8ff:febc:588f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1748 errors:0 dropped:0 overruns:0 frame:0
TX packets:1648 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1449962 (1.4 MB) TX bytes:280143 (280.1 KB)
Interrupt:19 Base address:0xc800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:474 errors:0 dropped:0 overruns:0 frame:0
TX packets:474 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:36080 (36.0 KB) TX bytes:36080 (36.0 KB)

wlan0 Link encap:Ethernet HWaddr 00:02:6f:8a:ae:13
inet addr:192.168.0.112 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::202:6fff:fe8a:ae13/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:2060 errors:0 dropped:0 overruns:0 frame:0
TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:305933 (305.9 KB) TX bytes:18312 (18.3 KB)

phoenix@phoenix:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 Ralink STA ESSID:"'phoenix'" Nickname:"RT2870STA"
Mode:Ad-Hoc Frequency=2.427 GHz Cell: 3E6:6D:7C:45:9C
Bit Rate=24 Mb/s
RTS thrff Fragment thrff
Link Quality=70/100 Signal level:0 dBm Noise level:-115 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

vboxnet0 no wireless extensions.


phoenix@phoenix:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 90
serial: 00:11:d8:bc:58:8f
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.11 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
resources: irq:19 ioport:c800(size=256) memory:ef003000-ef003fff memory:60000000-6001ffff
*-network:0
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:02:6f:8a:ae:13
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.0.112 multicast=yes wireless=Ralink STA
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

any ideas ?

Thanks

---

