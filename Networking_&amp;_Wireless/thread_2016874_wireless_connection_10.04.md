---
title: "wireless connection 10.04"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by daziel on 2012-07-04
10.04 
2.6.31-11-rt

The system could not configure the network at installation time.  I somehow got the wired connection to work, but not the wireless.
results from lspci, ifconfig, iwconfig, and lshw
Thanks
*******

lspci
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
	Kernel driver in use: sky2
	Kernel modules: sky2
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
*******

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:75:a1:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:ba:75:a1:1e  
          inet addr:169.254.7.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

pan0      Link encap:Ethernet  HWaddr 22:e7:4b:8d:63:be  
          inet6 addr: fe80::20e7:4bff:fe8d:63be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8585 (8.5 KB)

pan0:avahi Link encap:Ethernet  HWaddr 22:e7:4b:8d:63:be  
          inet addr:169.254.9.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:62:67:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:22:fb:62:67:da  
          inet addr:169.254.10.29  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FB-62-67-DA-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
*******

iwconfig
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
******

lshw
 *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:75:a1:1e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:d8200000-d8203fff ioport:4000(size=256)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:62:67:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d7100000-d7101fff

---

### Post by daziel on 2012-07-21
Any help?!

This is result from 
dmesg | grep iwl

[   14.541198] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   14.541200] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   14.542357] iwlagn 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.542366] iwlagn 0000:03:00.0: setting latency timer to 64
[   14.542393] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   14.602977] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.603058] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X
[   14.630406] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.664584] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   14.702939] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   14.845424] Registered led device: iwl-phy0::radio
[   14.845440] Registered led device: iwl-phy0::assoc
[   14.845457] Registered led device: iwl-phy0::RX
[   14.845471] Registered led device: iwl-phy0::TX

---

