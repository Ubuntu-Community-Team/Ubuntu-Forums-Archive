---
title: "No Wireless Internet Connection"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by rafanz on 2010-08-23
Hi,

I have been unsuccessful at connecting to the ADSL modem/Router in Automatic (DHCP) mode, where I have put in all addresses (gateway, DNS etc.). I am able to connect to the router if I manually set up the connection and am able to ping the device (192.168.1.1). However, although there is a connection indicated, I cannot view websites, nor the router setup page (through firefox). I have tried disabling IPv6, and think it may be a gateway issue. 

Please help as it would be much appreciated.  My system is a Toshiba laptop running Ubuntu 9.10, version 2.6.31-21-generic i686

The following information may help (most is without a wireless connection in automatic (DHCP mode), unless stated). 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:76:f5:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8408 (8.4 KB)  TX bytes:8408 (8.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:11:ce:77  
          inet6 addr: fe80::21b:9eff:fe11:ce77/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17901 (17.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-9E-11-CE-77-31-31-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig wlan0
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:76:f5:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8408 (8.4 KB)  TX bytes:8408 (8.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:11:ce:77  
          inet6 addr: fe80::21b:9eff:fe11:ce77/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17901 (17.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-9E-11-CE-77-31-31-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lshw

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:76:f5:e8
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:f0600000-f0603fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:11:ce:77
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0700000-f070ffff


The following is the output of iwlist wlan0 - once I have configured the settings to connect to the Router. 

wlan0     Scan completed :
          Cell 01 - Address: 00:21:63:86:D3:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"RTA1025W-86D302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004f5c36184
                    Extra: Last beacon: 2016ms ago
                    IE: Unknown: 000F52544131303235572D383644333032
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000


Cheers

RF

---

