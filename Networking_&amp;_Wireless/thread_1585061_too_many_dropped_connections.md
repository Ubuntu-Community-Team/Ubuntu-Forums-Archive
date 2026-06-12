---
title: "too many dropped connections"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by rolypolycat on 2010-09-30
Hello!

I'm running Lucid xubuntu. i have a netgear WG111v3 usb wireless card. The router and the modem recognize each other,. but the connection drops constantly.Other times it takes many tries to connect. There are 3 windows and one Xbox  users in my house, all on the same router. When I spoke with 2 different people at Radio Shack, I was told that the software on the router is Windows based, so the Windows modems get top priority over Linux, hence the dropped signals. 
I was advised I could do One of three things:
1. Buy another router, one that specifically recognizes every operating system. That way, we all get equal bandwith.
2. Buy an antennae that boosts the signal.
3. Buy a booster for the signal that one cable end plugs into the router,then the device into a power outlet; the other in any power outlet, and then hardwire that to my ethernet card in my computer, so the signal stays constant.
This is the output from the terminal: 

shell@the-cathouse:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:54:01:78
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:e000(size=256) memory:ff820000-ff820fff memory:ff800000-ff81ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:3f:0e:37:7f:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.30 multicast=yes wireless=IEEE 802.11bg
shell@the-cathouse:~$ifconfig 
wlan0     Link encap:Ethernet  HWaddr c0:3f:0e:37:7f:9f  
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c23f:eff:fe37:7f9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:455730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270337997 (270.3 MB)  TX bytes:279924195 (279.9 MB)

shell@the-cathouse:~$ 
shell@the-cathouse:~$ sudo iwlist scan
[sudo] password for shell: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:8F:2A:B8
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000046014bad80
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000C4E4554474541525F484F4D45
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1603051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8B0050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E8F2AB81021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001B574E5231303030763228576972656C6573732041502D322E344729100800020086103C000103

shell@the-cathouse:~$ 
Based on this information, what would be my best option. I can't run line all the way across the house to my computer; that would take 50-75 feet after winding it's way through the house.
I don't use the ethernet card although it's still in the machine. Could it interfere with the signal?
Any help is greatly appreciated. Thanks in advance!

---

### Post by kreggz on 2010-09-30
1.Try using another channel on the Wifi router
2. Try adjusting the WiFi routers antenna. 
3. you could also switch to NDISwrapper in which you may find you get better signal. 

Netgear adapters are very Linux friendly from what I have experienced. My Netgear adapter didn't work properly until about Ubuntu 9.04 where I stopped using NDISwrapper.

---

