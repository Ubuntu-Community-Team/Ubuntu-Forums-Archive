---
title: "Cannot connect to visible wireless networks through PCI or USB adapter"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by wouldhaveahole on 2010-05-26
Hello,
I have just installed ubuntu 10.04 for the first time, and am very new to all of it.
I am having alot of difficulty getting my wireless running.

I can see wireless networks through network manager on both my wireless card and USB adapter, however neither of them can connect to any of these networks.
The computer is an Acer Aspire 1890 and the adapter is an Alfa AWUS036H.

Here are some outputs:

lspci
```
bob@bob-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
bob@bob-laptop:~$ 

```

lsusb
```
bob@bob-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 008: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bob@bob-laptop:~$ 

```

lshw
```
bob@bob-laptop:~$ sudo lshw -C network
[sudo] password for bob: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:06:9b:d7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:17 memory:c8219000-c8219fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:82:fe:21
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5788-v3.01 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:16 memory:c8200000-c820ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:ca:33:8c:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
bob@bob-laptop:~$ 

```

iwlist scan
```
bob@bob-laptop:~$ sudo iwlist scan
[sudo] password for bob: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:04:A6:05:C2
                    ESSID:"BTHomeHub2-WCPZ"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 240ms ago
          Cell 02 - Address: 0A:21:04:A6:05:C2
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-52 dBm  
                    Extra: Last beacon: 180ms ago
          Cell 03 - Address: 00:24:B2:F8:86:7A
                    ESSID:"SKY62014"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=50/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 252ms ago
          Cell 04 - Address: 06:21:04:A6:05:C2
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-51 dBm  
                    Extra: Last beacon: 228ms ago
          Cell 05 - Address: 00:23:4E:AD:5A:9B
                    ESSID:"BTHomeHub2-CC5J"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 20ms ago
          Cell 06 - Address: 00:01:E3:F6:27:6F
                    ESSID:"TiscaliF6276F"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 740ms ago
                    Extra: Channel flags: INVALID 
          Cell 07 - Address: 00:21:63:76:F0:F2
                    ESSID:"monkey"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12116ms ago

wlan0     Scan completed :
          Cell 01 - Address: 06:21:04:A6:05:C2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dc3bb5119
                    Extra: Last beacon: 1636ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010020000000
          Cell 02 - Address: 00:24:B2:F8:86:7A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"SKY62014"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a82a939fd
                    Extra: Last beacon: 1632ms ago
                    IE: Unknown: 0008534B593632303134
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:21:04:A6:05:C2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-WCPZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dc3bc0f71
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 000F4254486F6D65487562322D5743505A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010020000000
          Cell 04 - Address: 0A:21:04:A6:05:C2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dc3bbc054
                    Extra: Last beacon: 1636ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010020000000
          Cell 05 - Address: 00:01:E3:F6:27:6F
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TiscaliF6276F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000157dc21d8
                    Extra: Last beacon: 396ms ago
                    IE: Unknown: 000D54697363616C69463632373646
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 070A474220010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD050010910400
          Cell 06 - Address: 00:23:4E:AD:5A:9B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-CC5J"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004b7895bb787
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 000F4254486F6D65487562322D4343354A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 07 - Address: 00:14:6C:F1:25:EC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"vickypark"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005069c9dc8a
                    Extra: Last beacon: 1072ms ago
                    IE: Unknown: 00097669636B797061726B
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bob@bob-laptop:~$ 

```

cat etc/network/interfaces
```
bob@bob-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

bob@bob-laptop:~$ 

```

ifconfig
```
bob@bob-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:82:fe:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:06:9b:d7  
          inet6 addr: fe80::212:f0ff:fe06:9bd7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:33 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1416 (1.4 KB)
          Interrupt:17 Base address:0xa000 Memory:c8219000-c8219fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28436 (28.4 KB)  TX bytes:28436 (28.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:33:8c:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bob@bob-laptop:~$ 

```

sudo dhclient eth1
```
bob@bob-laptop:~$ sudo dhclient eth1
[sudo] password for bob: 
There is already a pid file /var/run/dhclient.pid with pid 3282
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:12:f0:06:9b:d7
Sending on   LPF/eth1/00:12:f0:06:9b:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bob@bob-laptop:~$ 

```


Please help, I'm at a dead end for ideas. Already tried alot of solutions from others similar problems.

Regards
M

---

### Post by wouldhaveahole on 2010-05-26
Bump.
I've been trying to fix this all day :(
Is there some more information I should be providing to get some help quicker?

---

### Post by linuxonbute on 2010-05-26
> **wouldhaveahole said:**
> Bump.
I've been trying to fix this all day :(
Is there some more information I should be providing to get some help quicker?

maybe post result of

iwconfig

would help

---

### Post by wouldhaveahole on 2010-05-26
Thanks.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
```

---

### Post by linuxonbute on 2010-05-26
> **wouldhaveahole said:**
> Thanks.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
```

First unplug your usb adaptor.

wait a few seconds, run iwconfig again and post result

---

### Post by wouldhaveahole on 2010-05-26
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by linuxonbute on 2010-05-26
> **wouldhaveahole said:**
> ```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Okay do you have your own wireless router you want to connect to or not?

If not you can now try to connect to one of those which has no passphrase ( the ones with no padlock next to them )

If you have but it isn't shown you have either got it set so it doesn't transmit it's ESSID or you need to click on 'more networks' to see it.

---

### Post by wouldhaveahole on 2010-05-26
Thanks linuxonbute, can't say how long I've been trying to fix this.

When I choose an unsecured network it tries to connect for about 30 seconds before saying 'disconnected' again.

---

### Post by linuxonbute on 2010-05-26
> **wouldhaveahole said:**
> Thanks linuxonbute, can't say how long I've been trying to fix this.

When I choose an unsecured network it tries to connect for about 30 seconds before saying 'disconnected' again.

have you tried BTOpenzone i find it usually connects.

Do you have your own router?

---

### Post by wouldhaveahole on 2010-05-26
BTOpenzone does not connect.
Infact, I cannot connect to any wireless networks, and if done through the terminal they all return the No DHCPOFFERS line.

---

### Post by linuxonbute on 2010-05-26
> **wouldhaveahole said:**
> BTOpenzone does not connect.
Infact, I cannot connect to any wireless networks, and if done through the terminal they all return the No DHCPOFFERS line.

Are you just trying to connect to one of them or to your own router?

---

### Post by wouldhaveahole on 2010-05-26
I am trying to connect to BTOpenZone in this example.
But I have tried to connect to several other networks and faced the same problem. Other computers are able to connect to these networks fine, which makes me think it's a software issue. Furthermore I seem to be getting the same problem using the USB adapter, whereby no DHCP's are offered.

---

### Post by wouldhaveahole on 2010-05-27
Bump!

I am about to start another long day struggling to fix this.
I have read similar experiences where ubuntu is unable to obtain an i.p address from the DHCP servers, but nothing has worked yet. A post over at linux questions referred to wpa_supplicant sometimes needing to be set-up correctly before any connections can be established. I did have some very brief success with this, managing to connect to a WEP encrypted network however I was not receiving any data and nothing would load. I was well out of my depth and turned away from that avenue as it appeared to be getting no further.
Several hours on the irc channel have also failed to find a solution to the problem.... help please?

---

### Post by linuxonbute on 2010-05-27
Are you trying to use this at home and are you wanting to connect to your own wireless router?

---

### Post by wouldhaveahole on 2010-05-27
> **linuxonbute said:**
> Are you trying to use this at home and are you wanting to connect to your own wireless router?

I am trying to use this at home.
But I would also like to be able to connect to other networks, and I cannot currently connect to anything.

---

### Post by chili555 on 2010-05-27
With the USB device unplugged and safely locked in the drawer in the garage, reboot. Click the Network Manager icon. Do you see your network? When you click your network, are you asked for the encryption key? Does it try and fail?

I have seen some routers that can be set for a mixed WPA ***and*** WPA2 mode. Network Manager doesn't seem to be able to connect to it at all. If your router is set up like this, pick one mode or the other and then restart the router. Can you connect now?

What does this tell us?```
sudo cat /var/log/syslog | grep -i network
```Post the last 20 or so lines where it tries and fails to connect.

---

### Post by chili555 on 2010-05-27
I notice this:> Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)And I assume this is your network:> eth1      Scan completed :
          Cell 01 - Address: 00:21:04:A6:05:C2
                    ESSID:"BTHomeHub2-WCPZ"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 240ms ago
I am not at all sure the 2200BG does WPA. Check with:```
sudo iwlist eth1 auth
```Is that why you bought the USB device?

---

### Post by wouldhaveahole on 2010-05-27
Thank you so much for jumping in here chilli.

Wireless device well and truely hidden, and rebooted, still can't connect.

sudo cat /var/log/syslog | grep -i network:
```
 
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): carrier is OFF
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): now managed
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): bringing up device.
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): preparing device.
May 27 05:18:19 bob-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May 27 05:18:20 bob-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:06:08.0/net/eth0
May 27 05:18:20 bob-laptop NetworkManager: <info>  modem-manager is now available
May 27 05:18:20 bob-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May 27 05:18:20 bob-laptop NetworkManager: <info>  Trying to start the supplicant...
May 27 05:18:20 bob-laptop NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
May 27 05:18:21 bob-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
May 27 05:18:21 bob-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto BTOpenzone'
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto BTOpenzone' requires no security.  No secrets needed.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Config: added 'ssid' value 'BTOpenzone'
May 27 05:20:11 bob-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May 27 05:20:11 bob-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTOpenzone'.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 27 05:20:11 bob-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
May 27 05:20:11 bob-laptop NetworkManager: <info>  dhclient started with pid 1292
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
May 27 05:20:11 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
May 27 05:20:12 bob-laptop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
May 27 05:20:57 bob-laptop NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
May 27 05:20:57 bob-laptop NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1292
May 27 05:20:57 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 27 05:20:57 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
May 27 05:20:57 bob-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
May 27 05:20:57 bob-laptop NetworkManager: <info>  Activation (eth1) failed for access point (BTOpenzone)
May 27 05:20:57 bob-laptop NetworkManager: <info>  Marking connection 'Auto BTOpenzone' invalid.
May 27 05:20:57 bob-laptop NetworkManager: <info>  Activation (eth1) failed.
May 27 05:20:57 bob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 27 05:20:57 bob-laptop NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
May 27 05:20:57 bob-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0).
bob@bob-laptop:~$ 

```

I have also done another iwlist scan to show my home network - BTHomeHub-332E
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:04:A6:05:C2
                    ESSID:"BTHomeHub2-WCPZ"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 272ms ago
          Cell 02 - Address: 06:21:04:A6:05:C2
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    Extra: Last beacon: 268ms ago
          Cell 03 - Address: 0A:21:04:A6:05:C2
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    Extra: Last beacon: 264ms ago
          Cell 04 - Address: 00:23:4E:AD:5A:9B
                    ESSID:"BTHomeHub2-CC5J"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 404ms ago
          Cell 05 - Address: 00:21:63:76:F0:F2
                    ESSID:"monkey"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 11788ms ago
          Cell 06 - Address: 00:1F:9F:D6:3E:05
                    ESSID:"O2wireless376448"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-78 dBm  
                    Extra: Last beacon: 12220ms ago
          Cell 07 - Address: 0A:21:04:D8:31:42
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    Extra: Last beacon: 32ms ago
          Cell 08 - Address: 00:21:04:D8:31:42
                    ESSID:"BTHomeHub2-GP69"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 40ms ago
          Cell 09 - Address: 06:21:04:D8:31:42
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm  
                    Extra: Last beacon: 16ms ago
          Cell 10 - Address: 00:14:6C:F1:25:EC
                    ESSID:"vickypark"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 136ms ago
          Cell 11 - Address: 00:19:7D:53:1D:CA
                    ESSID:"Livebox-8930"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 13264ms ago
          Cell 12 - Address: 02:24:17:C9:BB:04
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 13128ms ago
          Cell 13 - Address: 00:22:3F:12:95:00
                    ESSID:"Neilcott Wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 164ms ago
          Cell 14 - Address: 00:18:F6:5F:E8:53
                    ESSID:"BTHomeHub-332E"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm  
                    Extra: Last beacon: 504ms ago
          Cell 15 - Address: 00:1E:2A:11:1A:88
                    ESSID:"virgin broadband"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7896ms ago


```

And finally the result from sudo iwlist eth1 auth:
```
eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : yes
          Current Privacy invoked : yes

```

---

### Post by chili555 on 2010-05-27
> I have also done another iwlist scan to show my home network - BTHomeHub-332E
> ESSID:"BTHomeHub-332E"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    [COLOR="Red"]Encryption key:on[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm Aside from a very low signal strength, it looks like WEP encryption is in place. However, Network Manager reports:> Activation (eth1/wireless): connection 'Auto [COLOR="Red"]BTOpenzone[/COLOR]' requires no security.  No secrets needed.
May 27 05:10:49 bob-laptop NetworkManager: <info>  Config: added 'ssid' value 'BTOpenzone'
Did you click the wrong network?

---

### Post by wouldhaveahole on 2010-05-27
My router is WEP encrypted.

However I would also like to able to connect to BTOpenzone which has no encryption. For future reference I will only now try to connect to BTOpenzone.

---

### Post by chili555 on 2010-05-27
BTopenzone, unfortunately, has even lower signal strength. May I see:```
dmesg | grep ipw
```Thanks.

---

### Post by wouldhaveahole on 2010-05-28
Thank again for all your help Chilli,
I am away until Sunday afternoon though so I will have to get back to this then.

---

### Post by chili555 on 2010-05-28
Have a great weekend; see you then.

---

### Post by wouldhaveahole on 2010-05-30
Let's get back too this then :)

dmesg | grep ipw
```
bob@bob-laptop:~$ dmesg | grep ipw
[    6.169435] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    6.169439] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    6.169514] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.171575] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    6.171631] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[    7.097139] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 5605.564248] ipw2200 0000:06:03.0: PCI INT A disabled
[ 5606.796169] ipw2200 0000:06:03.0: enabling device (0000 -> 0002)
[ 5606.796173] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5606.796185] ipw2200 0000:06:03.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[ 5606.796211] ipw2200 0000:06:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 5606.796219] ipw2200 0000:06:03.0: restoring config space at offset 0x1 (was 0x2900002, writing 0x2900016)
bob@bob-laptop:~$ 

```

---

### Post by wouldhaveahole on 2010-05-31
Any ideas/next steps Chili? I'm around today to keep cracking at this one if you can help :)

---

### Post by chili555 on 2010-05-31
Everything looks pretty normal. The only thing I can suggest is that BTopenzone has very low signal strength:> Cell 04 - Address: 06:21:04:A6:05:C2
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    [COLOR="Red"]Quality=46/100[/COLOR]  Signal level=-51 dBm  
                    Extra: Last beacon: 228ms ago
My card that uses ipw2200, an Intel 2915ABG, has difficulty connecting below about 50/100; if it connects, it has trouble staying connected. 

Do you feel this scan is accurate? I notice you scanned other networks at 78/100, so I'd surmise it is accurate.

Can you connect to BTFON that is unencrypted at 77/100?

---

### Post by wouldhaveahole on 2010-05-31
I trust the scan is accurate, and cannot connect to BTFon either.
What is puzzling me is that were it just signal strength that were the issue, I would expect to be able to connect using the USB adapter. However the USB adapter has exactly the same problem.
I am considering trying to reinstall an older version of ubuntu to see if this will work.

---

### Post by Talon2 on 2010-05-31
> **wouldhaveahole said:**
> My router is WEP encrypted.



My recommendation is to set your wifi router/ap to unsecure for now.  Once you have things working you can look at going to WPA2 security as your best option.  Security adds a variable you don't need to be dealing with right now so taking it out of the equation is a good idea.  I've seen situations where WEP security is the cause of problems such as this because it is not supported by all hardware and software.  This isn't just a Linux issue.

Good luck.

---

### Post by wouldhaveahole on 2010-05-31
> **Talon2 said:**
> My recommendation is to set your wifi router/ap to unsecure for now.  Once you have things working you can look at going to WPA2 security as your best option.  Security adds a variable you don't need to be dealing with right now so taking it out of the equation is a good idea.  I've seen situations where WEP security is the cause of problems such as this because it is not supported by all hardware and software.  This isn't just a Linux issue.

Good luck.

Hi Talon,
thanks for the help, and I will definitely be using WPA2 when this is solved. However the problem is not related to encryption as I cannot currentley connect to any unencrypted networks either

---

### Post by Yeeha on 2010-05-31
I had similar problem and i turned off bluetooth and suddenly i was able to connect again. If it will start working then tell, because if thats the case then my problem isnt that rare and ubuntu devs will know about it.

---

### Post by wouldhaveahole on 2010-05-31
> **Yeeha said:**
> I had similar problem and i turned off bluetooth and suddenly i was able to connect again. If it will start working then tell, because if thats the case then my problem isnt that rare and ubuntu devs will know about it.

Thanks for the tip, but Bluetooth is off and i still cannot connect.

A quick sum up then:
I cannot connect to any wireless connections: Encrypted/Unencrypted, Weak Signal/Strong Signal.
The problem appears to be in receiving an i.p address from the DHCP client.
The only time I have ever had it successfully connect to a network was after manually editing the wpa_supplicant.conf file, however I still could not load any web pages.
I have tried Ubuntu 8.04 and have the same problem.
I have tried reinstalling Ubuntu 10.04 and the problem persists
I have the same problem trying to connect through a RTL8187 USB device.

I can 'create' a wireless network, and other computers can connect to it.
BUT - I cannot connect to a network established by my other computer

Any new ideas?
Beginning to loose hope now

---

