---
title: "Roku box sees my LAN; won't connect. Using Wicd &amp; Firestarter"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by watchpocket on 2010-11-14
I'm setting up a desktop home LAN for the first time, so I can use a Roku box. Been reading wireless-related ubuntu tutorials for a few days now. 

At the moment I'm using Wicd (not NetworkManager, tho I was using it previously) and Firestarter.  My Roku box can see my network, but won't connect to it.  

I have no router, and I'm assuming I don't need one.

The somewhat lengthy output of the following commands . . .

```
 

sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|usb|witch|wl'; iwconfig; cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod 


```. . . appears here:

```


  *-network               
       description: Ethernet interface
       product: 82567LF-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:27:0e:01:b2:89
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-5 ip=67.81.187.226 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:f100(size=32)
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wmaster0
       version: 01
       serial: 00:24:01:11:e5:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.2 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:e3100000-e310ffff
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:65:6E:F6
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"hottub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009d6f63b4f
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 0006686F74747562
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020004
          Cell 02 - Address: 00:22:75:BA:2E:8F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Odyssey E1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000105ca80344
                    Extra: Last beacon: 430ms ago
                    IE: Unknown: 000A4F647973736579204531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F0000000000000000000000000000000000000000
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B0001031047001000000000000000011000002275BA2E8F1021001242656C6B696E20436F72706F726174696F6E1023000C463644343233302D3420763310240007332E30302E30331042000E31323933323432333035313433331054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD050050F20500
          Cell 03 - Address: 00:25:9C:1E:98:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"rm929"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000508ca699af
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 0005726D393239
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
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
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
          Cell 04 - Address: 00:25:9C:D9:DA:A5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"mcs23nov"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f758403e4
                    Extra: Last beacon: 110ms ago
                    IE: Unknown: 00086D637332336E6F76
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700103719AB0854F5BB8B0B5134FB690A20FE102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180201F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 05 - Address: 00:13:49:6E:18:27
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"LK420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003afd1ed11c3
                    Extra: Last beacon: 130ms ago
                    IE: Unknown: 00054C4B343230
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 0706415420010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4140027A4000042435E0062322F00
          Cell 06 - Address: 00:1F:90:B7:7F:9C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"2XPS5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000069f5181
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 00053258505335
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 07 - Address: 06:93:EB:81:54:74
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"wicd-wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 26752420ms ago
                    IE: Unknown: 0009776963642D77696669
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
          Cell 08 - Address: 00:22:3F:D7:53:FC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"avillamar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020f4471c183
                    Extra: Last beacon: 10ms ago
                    IE: Unknown: 00096176696C6C616D6172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:1A:70:DE:A5:96
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"apt_network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000222e7902a2c
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000B6170745F6E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F0100000000000000000000000000000000000000
          Cell 10 - Address: 00:11:50:72:27:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"keebler house"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000781681072
                    Extra: Last beacon: 110ms ago
                    IE: Unknown: 000D6B6565626C657220686F757365
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 11 - Address: 00:23:69:AD:03:6E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Penelope"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f374cbe5e
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 000850656E656C6F7065
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A344D333439371054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:25:9C:39:3C:6E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Kish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000081c1e28f46
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 00044B697368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700106AFB34594A025A1C3D89D46E347ABD0D102100074C696E6B737973102300075752543331304E102400063132333435361042000234321054000800060050F2040001101100075752543331304E100800020084
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
     wireless-mode ad-hoc
     wireless-essid wicd-wifi
     address 192.168.0.2
     gateway 192.168.0.1
     netmask 255.255.255.0

#     wireless-key 1234567890
#     wireless-channel 6






DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce GTS 250] [10de:0615] (rev a2)
02:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)
02:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0488:00df Cirque Corp. 
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
H/W path           Device      Class       Description
======================================================
                               system      Wild Dog Performance
/0                             bus         DP45SG
/0/0                           memory      64KiB BIOS
/0/4                           processor   Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz
/0/4/5                         memory      32KiB L1 cache
/0/4/6                         memory      6MiB L2 cache
/0/2c                          memory      8GiB System Memory
/0/2c/0                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/1                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/2                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/2c/3                        memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/100                         bridge      4 Series Chipset DRAM Controller
/0/100/1                       bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                     display     G92 [GeForce GTS 250]
/0/100/19          eth0        network     82567LF-2 Gigabit Network Connection
/0/100/1a                      bus         82801JI (ICH10 Family) USB UHCI Controller #4
/0/100/1a.1                    bus         82801JI (ICH10 Family) USB UHCI Controller #5
/0/100/1a.2                    bus         82801JI (ICH10 Family) USB UHCI Controller #6
/0/100/1a.7                    bus         82801JI (ICH10 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia  82801JI (ICH10 Family) HD Audio Controller
/0/100/1d                      bus         82801JI (ICH10 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801JI (ICH10 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801JI (ICH10 Family) USB UHCI Controller #3
/0/100/1d.7                    bus         82801JI (ICH10 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/0                    bus         FW322/323
/0/100/1e/3        wmaster0    network     AR2413 802.11bg NIC
/0/100/1f                      bridge      82801JIR (ICH10R) LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801JI (ICH10 Family) SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        1TB ST31000528AS
/0/100/1f.2/0/1    /dev/sda1   volume      13GiB EXT3 volume
/0/100/1f.2/0/2    /dev/sda2   volume      7628MiB Linux swap volume
/0/100/1f.2/0/3    /dev/sda3   volume      910GiB EXT3 volume
/0/100/1f.2/1      /dev/cdrom  disk        CDDVDW SH-S223C
/0/100/1f.2/0.0.0  /dev/scd1   disk        CDDVDW SH-S223C
/0/100/1f.3                    bus         82801JI (ICH10 Family) SMBus Controller
Linux rj.rjbox.net 2.6.31-22-generic #68-Ubuntu SMP Tue Oct 26 16:37:17 UTC 2010 x86_64 GNU/Linux
[    0.000000] No NUMA configuration found
[    0.000000] found SMP MP-table at [ffff8800000fd4e0] fd4e0
[    0.000000] No AGP bridge found
[    0.632909] ACPI: No dock devices found.
[    0.638139] usbcore: registered new interface driver usbfs
[    0.638139] usbcore: registered new interface driver hub
[    0.638139] usbcore: registered new device driver usb
[    0.690004] Switched to high resolution mode on CPU 0
[    0.691422] Switched to high resolution mode on CPU 1
[    0.691437] Switched to high resolution mode on CPU 3
[    0.691493] Switched to high resolution mode on CPU 2
[    0.711426] pnp: PnP ACPI: found 11 devices
[    4.990061] usb usb1: configuration #1 chosen from 1 choice
[    4.990079] hub 1-0:1.0: USB hub found
[    5.010042] usb usb2: configuration #1 chosen from 1 choice
[    5.010058] hub 2-0:1.0: USB hub found
[    5.010283] usb usb3: configuration #1 chosen from 1 choice
[    5.010300] hub 3-0:1.0: USB hub found
[    5.010456] usb usb4: configuration #1 chosen from 1 choice
[    5.010474] hub 4-0:1.0: USB hub found
[    5.010625] usb usb5: configuration #1 chosen from 1 choice
[    5.010641] hub 5-0:1.0: USB hub found
[    5.010789] usb usb6: configuration #1 chosen from 1 choice
[    5.010804] hub 6-0:1.0: USB hub found
[    5.010960] usb usb7: configuration #1 chosen from 1 choice
[    5.010975] hub 7-0:1.0: USB hub found
[    5.011122] usb usb8: configuration #1 chosen from 1 choice
[    5.011139] hub 8-0:1.0: USB hub found
[    5.011206] PNP: No PS/2 controller found. Probing ports directly.
[    5.015532] device-mapper: multipath: version 1.1.0 loaded
[    5.015536] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.017024] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.590006] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.770302] usb 3-1: configuration #1 chosen from 1 choice
[    6.050006] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    6.159839] usbcore: registered new interface driver hiddev
[    6.173460] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
[    6.173517] generic-usb 0003:046D:C040.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    6.173530] usbcore: registered new interface driver usbhid
[    6.173532] usbhid: v2.6:USB HID core driver
[    6.227322] usb 3-2: configuration #1 chosen from 1 choice
[    6.270671] input: Cirque GlidePoint as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    6.270715] generic-usb 0003:0488:00DF.0002: input,hidraw1: USB HID v1.10 Keyboard [Cirque GlidePoint] on usb-0000:00:1a.0-2/input0
[    6.282394] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:27:0e:01:b2:89
[    6.282396] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    6.282421] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[   18.797794] lp: driver loaded but no devices found
[   19.081816] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.081856] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.081895] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.081932] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.081971] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.082009] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.082046] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   19.212178] ath5k 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.212210] ath5k 0000:02:03.0: registered as 'phy0'
[   19.484435] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.794400] ath: EEPROM regdomain: 0x10
[   19.794401] ath: EEPROM indicates we should expect a direct regpair map
[   19.794403] ath: Country alpha2 being used: CO
[   19.794404] ath: Regpair used: 0x10
[   19.799173] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   19.951930] wlan0: Trigger new scan to find an IBSS to join
[   20.074078] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.162719] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.253316] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.344133] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.468475] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.551632] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.639477] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.721475] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.812471] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   20.902444] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   21.030423] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   21.030426] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.031035] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.011262] wlan0: Trigger new scan to find an IBSS to join
[   26.132579] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.207056] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.291817] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.368906] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.466028] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.549210] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.631343] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.709986] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.790592] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   26.872908] ath5k phy0: bf=ffff8802029b6d00 bf_skb=(null)
[   28.950010] wlan0: Trigger new scan to find an IBSS to join
[   29.867166] wlan0: Creating new IBSS network, BSSID 06:93:eb:81:54:74
[   29.970004] wlan0: no IPv6 routers present
[   31.320003] eth0: no IPv6 routers present
[   59.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[   91.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  122.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  153.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  183.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  214.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  245.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  276.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  308.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  338.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  369.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  400.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  431.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  462.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  493.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  524.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  555.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  586.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  603.554568] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=98.176.181.137 DST=67.81.187.226 LEN=95 TOS=0x00 PREC=0x00 TTL=119 ID=1984 PROTO=UDP SPT=29670 DPT=51413 LEN=75 
[  617.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  648.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  679.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  710.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  741.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  772.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  803.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  834.982457] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  866.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  880.165841] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[  880.404777] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  880.782835] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=29505 WINDOW=8192 RES=0x00 SYN URGP=0 
[  896.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  927.953755] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  958.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  990.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1021.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1051.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1082.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1113.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1144.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1176.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1207.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1226.012534] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=218.89.168.253 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=104 ID=5736 PROTO=TCP SPT=42625 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1237.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1269.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1299.953758] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1330.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1361.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1392.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1423.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1450.605093] ath5k phy0: unsupported jumbo
[ 1454.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1486.010011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1517.011261] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1547.953755] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1578.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1609.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1640.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1642.500992] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1671.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1702.953758] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1734.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1764.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1795.951117] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1827.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1857.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1888.950014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1914.366387] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1914.386098] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=9090 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1914.416151] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=8008 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1914.424784] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=73 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1914.438463] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=7212 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1919.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1950.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1981.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2012.953759] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2044.011260] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2075.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2105.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2136.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2167.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2198.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2209.137063] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=73 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2229.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2260.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2291.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2322.982510] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2353.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2384.953758] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2415.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2446.950011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2477.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2508.952039] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2539.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2570.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2601.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2633.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2664.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2695.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2726.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2735.174637] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=73 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2735.640217] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=79.142.69.222 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=29505 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2757.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2788.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2819.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2849.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2880.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2912.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2943.011260] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2973.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3004.755295] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3004.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3006.144600] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3035.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3066.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3097.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3128.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3159.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3190.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3222.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3253.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3284.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3315.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3346.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3377.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3408.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3438.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3469.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3500.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3531.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3562.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3593.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3624.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3655.950980] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3687.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3718.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3749.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3779.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3810.953759] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3841.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3868.722146] ath5k phy0: unsupported jumbo
[ 3872.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3903.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3934.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3965.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3997.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4027.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4058.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4090.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4121.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4152.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4177.641847] ath5k phy0: unsupported jumbo
[ 4183.040935] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4214.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4245.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4275.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4307.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4337.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4368.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4400.020006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4431.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4462.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4493.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4524.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4555.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4586.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4617.010036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4642.820197] ath5k phy0: unsupported jumbo
[ 4648.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4679.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4710.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4741.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4772.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4803.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4834.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4865.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4896.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4926.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4957.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4989.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5020.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5045.760921] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=78.25.24.209 DST=67.81.187.226 LEN=93 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=50323 DPT=51413 LEN=73 
[ 5051.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5082.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5113.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5144.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5175.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5205.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5236.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5268.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5299.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5329.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5360.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5391.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5422.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5454.011258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5485.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5515.914479] ath5k phy0: unsupported jumbo
[ 5516.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5547.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5578.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5609.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5640.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5671.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5701.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5733.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5763.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5794.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5826.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5857.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5888.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5919.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5950.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5981.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6011.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6042.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6073.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6091.284120] ath5k phy0: unsupported jumbo
[ 6104.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6135.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6166.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6197.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6228.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6259.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6291.040005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6306.004734] ath5k phy0: unsupported jumbo
[ 6322.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6353.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6383.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6414.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6445.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6476.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6507.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6538.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6570.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6600.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6632.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6663.011290] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6694.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6725.010011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6755.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6786.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6817.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6848.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6879.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6880.030049] ath5k phy0: noise floor calibration failed (2412MHz)
[ 6892.631665] ath5k phy0: unsupported jumbo
[ 6910.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6941.045649] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6941.049012] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6941.053798] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=7212 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6941.058037] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6941.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6972.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7003.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7034.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7065.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7096.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7128.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7158.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7189.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7220.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7251.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7282.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7313.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7344.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7375.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7406.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7438.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7468.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7485.021744] ath5k phy0: unsupported jumbo
[ 7500.038021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7531.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7561.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7592.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7623.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7654.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7686.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7716.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7747.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7778.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7810.039357] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7841.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7871.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7896.179992] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7896.191765] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=9000 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7896.202896] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=9090 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7896.215396] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7896.226550] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7902.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7933.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7964.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7995.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8026.950011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8057.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8088.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8120.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8151.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8182.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8213.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8243.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8274.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8305.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8336.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8367.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8398.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8429.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8460.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8491.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8522.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8554.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8584.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8615.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8646.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8652.628228] ath5k phy0: unsupported jumbo
[ 8673.469963] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.53.128.61 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=103 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 8677.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8708.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8739.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8770.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8801.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8832.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8864.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8894.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8925.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8956.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8987.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9018.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9049.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9080.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9111.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9142.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9174.021258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9205.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9235.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9266.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9297.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9328.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9359.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9391.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9421.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9452.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9484.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9514.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9545.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9559.111280] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=218.60.132.111 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=100 ID=256 PROTO=TCP SPT=6000 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 9576.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9607.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9638.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9670.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9701.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9706.402702] ath5k phy0: unsupported jumbo
[ 9732.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9763.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9794.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9825.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9856.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9879.972279] ath5k phy0: unsupported jumbo
[ 9887.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9918.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9948.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 9979.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10011.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10042.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10073.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10104.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10135.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10166.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10197.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10227.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10258.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10289.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10321.040017] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10352.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10383.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10414.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10428.731075] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[10428.734913] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
[10428.739528] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=7212 WINDOW=8192 RES=0x00 SYN URGP=0 
[10428.744393] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[10432.463479] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=9415 WINDOW=8192 RES=0x00 SYN URGP=0 
[10432.478498] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=2479 WINDOW=8192 RES=0x00 SYN URGP=0 
[10432.487962] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=3246 WINDOW=8192 RES=0x00 SYN URGP=0 
[10432.502559] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=9090 WINDOW=8192 RES=0x00 SYN URGP=0 
[10445.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10476.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10506.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10538.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10569.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10599.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10630.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10661.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10692.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10723.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10754.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10785.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10816.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10848.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10872.723372] ath5k phy0: unsupported jumbo
[10879.011259] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10909.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10940.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10971.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[10988.480134] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=122.227.164.71 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 PROTO=TCP SPT=6000 DPT=8000 WINDOW=16384 RES=0x00 SYN URGP=0 
[10988.480152] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=122.227.164.71 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 PROTO=TCP SPT=6000 DPT=7212 WINDOW=16384 RES=0x00 SYN URGP=0 
[11002.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11033.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11064.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11095.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11126.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11157.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11188.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11220.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11225.354323] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=221.1.220.185 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[11231.488924] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=221.1.220.185 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 DF PROTO=TCP SPT=12200 DPT=1022 WINDOW=8192 RES=0x00 SYN URGP=0 
[11251.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11282.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11313.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11344.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11375.010006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11406.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11437.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11467.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11498.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11529.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11560.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11591.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11622.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11654.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11684.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11715.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11747.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11778.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11809.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11840.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11870.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11901.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11932.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11963.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[11995.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12025.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12056.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12087.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12118.953758] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12149.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12180.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12211.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12242.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12273.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12304.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12335.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12366.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12397.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12428.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12459.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12490.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12522.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12553.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12584.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12615.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12646.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12677.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12706.443297] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=64.71.155.117 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=62469 PROTO=TCP SPT=65468 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0 
[12708.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12739.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12769.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12801.010037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12832.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12862.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12893.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12924.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12955.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[12986.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13017.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13048.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13079.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13111.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13141.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13172.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13203.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13234.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13265.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13296.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13327.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13358.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13390.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13421.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13451.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13482.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13513.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13544.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13575.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13606.950011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13638.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13668.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13699.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13730.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13761.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13793.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13823.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13854.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13885.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13916.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13947.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[13978.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14009.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14041.010006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14072.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14103.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14134.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14165.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14195.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14226.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14258.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14289.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14320.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14351.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14382.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14413.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14444.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14474.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14506.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14536.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14568.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14599.011258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14629.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14660.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14691.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14722.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14753.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14784.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14815.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14846.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14878.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14907.631304] ath5k phy0: unsupported jumbo
[14909.044237] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14939.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[14970.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15001.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15032.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15064.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15095.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15126.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15157.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15188.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15219.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15250.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15258.479590] ath5k phy0: unsupported jumbo
[15281.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15312.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15343.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15374.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15405.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15435.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15466.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15497.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15528.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15559.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15590.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15622.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15652.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15684.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15715.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15746.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15777.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15808.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15839.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15870.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15900.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15931.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15945.701256] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=87.91.14.145 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16072 DF PROTO=TCP SPT=54853 DPT=3389 WINDOW=65535 RES=0x00 SYN URGP=0 
[15948.759200] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=87.91.14.145 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16473 DF PROTO=TCP SPT=54853 DPT=3389 WINDOW=65535 RES=0x00 SYN URGP=0 
[15963.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[15993.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16024.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16055.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16086.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16117.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16148.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16179.953758] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16210.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16241.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16268.755814] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=218.60.132.111 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=100 ID=256 PROTO=TCP SPT=6000 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0 
[16272.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16303.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16334.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16365.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16396.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16427.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16458.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16490.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16520.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16551.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16583.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16614.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16644.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16675.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16706.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16737.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16769.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16799.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16830.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16861.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16892.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16923.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16954.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[16985.953756] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17016.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17048.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17078.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17109.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17140.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17171.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17202.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17233.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17264.982516] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17296.050028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17326.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17358.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17388.982154] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17420.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17451.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17482.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17513.040142] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17544.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17555.344888] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[17555.362084] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=9415 WINDOW=8192 RES=0x00 SYN URGP=0 
[17555.396131] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=9000 WINDOW=8192 RES=0x00 SYN URGP=0 
[17555.398535] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[17555.416104] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.199.147 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8088 WINDOW=8192 RES=0x00 SYN URGP=0 
[17575.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17606.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17636.980909] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17668.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17699.016027] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17730.033867] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17761.011258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17792.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17823.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17854.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17885.010012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17915.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17946.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[17977.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18008.951180] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18040.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18071.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18102.050019] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18133.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18164.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18195.011288] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18226.011261] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18256.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18287.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18318.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18349.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18380.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18411.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18442.982606] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18474.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18505.010038] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18536.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18567.011259] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18597.951751] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18628.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18664.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18695.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18726.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18757.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18788.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18819.040018] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18849.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18880.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18888.749348] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=78.25.24.209 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=63083 DF PROTO=TCP SPT=38641 DPT=51413 WINDOW=5840 RES=0x00 SYN URGP=0 
[18891.761845] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=78.25.24.209 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=63084 DF PROTO=TCP SPT=38641 DPT=51413 WINDOW=5840 RES=0x00 SYN URGP=0 
[18897.749042] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=78.25.24.209 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=63085 DF PROTO=TCP SPT=38641 DPT=51413 WINDOW=5840 RES=0x00 SYN URGP=0 
[18912.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18943.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[18944.507923] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=2479 WINDOW=8192 RES=0x00 SYN URGP=0 
[18944.520343] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=3246 WINDOW=8192 RES=0x00 SYN URGP=0 
[18944.531135] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=9090 WINDOW=8192 RES=0x00 SYN URGP=0 
[18944.543549] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=9000 WINDOW=8192 RES=0x00 SYN URGP=0 
[18944.557332] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.218.204.110 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=102 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[18973.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19004.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19035.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19066.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19097.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19128.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19160.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19190.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19222.040020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19253.010006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19284.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19315.040020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19346.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19377.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19408.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19439.011256] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19470.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19501.010011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19532.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19563.040022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19585.049821] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=18.181.0.31 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=43473 DF PROTO=TCP SPT=54234 DPT=13 WINDOW=5840 RES=0x00 SYN URGP=0 
[19588.046004] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=18.181.0.31 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=43474 DF PROTO=TCP SPT=54234 DPT=13 WINDOW=5840 RES=0x00 SYN URGP=0 
[19588.051091] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=18.181.0.31 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=32394 DF PROTO=TCP SPT=41685 DPT=17 WINDOW=5840 RES=0x00 SYN URGP=0 
[19591.046471] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=18.181.0.31 DST=67.81.187.226 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=32395 DF PROTO=TCP SPT=41685 DPT=17 WINDOW=5840 RES=0x00 SYN URGP=0 
[19594.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19625.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19656.046635] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19687.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19687.097570] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45460 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19687.099257] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=1500 TOS=0x00 PREC=0x00 TTL=49 ID=45461 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK URGP=0 
[19687.099642] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=1500 TOS=0x00 PREC=0x00 TTL=49 ID=45462 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK URGP=0 
[19690.096744] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45464 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19696.097252] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45465 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19708.096547] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45466 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19718.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19732.096024] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45467 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19748.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19779.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19780.096247] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45468 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19810.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19841.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19872.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19876.095852] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=198.171.79.36 DST=67.81.187.226 LEN=820 TOS=0x00 PREC=0x00 TTL=49 ID=45469 DF PROTO=TCP SPT=80 DPT=41794 WINDOW=7686 RES=0x00 ACK PSH URGP=0 
[19903.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19934.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19965.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[19996.953760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20027.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20058.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20090.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20121.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20152.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20183.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20214.040010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20245.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20275.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20306.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20337.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20368.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20399.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20430.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20461.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20492.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20506.707681] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=221.1.220.185 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
[20513.849513] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=221.1.220.185 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[20522.143411] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=221.1.220.185 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 DF PROTO=TCP SPT=12200 DPT=1022 WINDOW=8192 RES=0x00 SYN URGP=0 
[20523.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20554.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20585.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20616.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20647.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20678.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20709.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20740.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20771.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20802.980021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20812.229260] ath5k phy0: unsupported jumbo
[20834.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20864.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20895.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20927.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20958.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[20989.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21020.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21022.486467] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.53.128.61 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=103 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[21033.762431] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=58.53.128.61 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=103 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[21051.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21082.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21134.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21164.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21195.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21226.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21257.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21288.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21319.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21350.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21366.630143] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=188.165.64.220 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[21381.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21412.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21444.040010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21475.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21506.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21537.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21568.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21599.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21630.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21660.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21691.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21723.011289] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21754.021257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21769.200153] ath5k phy0: unsupported jumbo
[21784.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21815.982505] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21846.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21877.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21908.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21935.102711] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=95.211.132.150 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=64581 PROTO=TCP SPT=23257 DPT=8443 WINDOW=65535 RES=0x00 SYN URGP=0 
[21939.950011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[21971.011293] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22002.011257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22032.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22063.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22094.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22125.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22156.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22187.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22218.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22250.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22280.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22311.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22342.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22373.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22404.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22435.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22466.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22497.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22528.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22560.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22590.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22607.183210] ath5k phy0: unsupported jumbo
[22621.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22652.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22683.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22714.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22745.953755] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22776.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22807.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22839.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22870.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22901.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22932.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22963.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[22994.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23025.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23056.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23086.982508] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23117.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23148.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23179.982509] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23211.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23242.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23273.040136] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23304.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23335.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23366.011258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23396.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23427.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23458.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23490.046386] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23521.011258] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23552.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23583.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23614.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23645.010012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23675.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23706.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23737.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23768.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23799.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23830.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23861.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23892.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23923.953759] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23954.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[23985.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24017.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24048.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24079.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24110.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24141.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24172.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24203.040008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24209.283185] ath5k phy0: unsupported jumbo
[24233.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24264.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24296.040026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24327.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24358.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24389.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24420.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24451.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24481.950005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24512.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24543.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24575.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24606.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24637.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24668.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24699.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24730.048462] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24761.040016] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24791.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24822.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24854.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24885.011260] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24915.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24946.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[24947.342132] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
[24947.344331] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=7212 WINDOW=8192 RES=0x00 SYN URGP=0 
[24947.347410] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=222.186.26.88 DST=67.81.187.226 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[24977.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25008.980005] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25039.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25070.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25101.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25132.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25163.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25194.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25225.980011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25256.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25287.205071] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=24.222.139.134 DST=67.81.187.226 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=16542 DF PROTO=TCP SPT=54607 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[25287.982506] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25290.196503] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=24.222.139.134 DST=67.81.187.226 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=16792 DF PROTO=TCP SPT=54607 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[25296.200466] Inbound IN=eth0 OUT= MAC=00:27:0e:01:b2:89:00:05:00:e6:11:6d:08:00 SRC=24.222.139.134 DST=67.81.187.226 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=17260 DF PROTO=TCP SPT=54607 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[25318.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25349.950010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25381.040009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25411.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25442.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25473.953757] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25504.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25535.950007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25566.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25597.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25629.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25660.040006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25691.010009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25721.980010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25752.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25783.981625] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25815.010007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25846.011262] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25877.010010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25907.950006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25938.950009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[25969.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26001.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26032.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26063.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26094.040013] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26125.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26156.040014] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26186.980006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26217.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26249.040007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26280.038342] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26311.010006] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26342.040011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26373.040015] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26404.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26435.040012] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26466.011259] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26496.953759] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26528.010008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26567.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26598.950008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26629.980009] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26661.040010] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26691.980007] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26722.980008] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[26753.982507] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wicd-wifi"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 06:93:EB:81:54:74   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist twl4030_wdt
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
10: PCI 19.0: 0200 Ethernet controller                          
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_10cd
  Unique ID: rBUF.0N_I7wohxJD
  SysFS ID: /devices/pci0000:00/0000:00:19.0
  SysFS BusID: 0000:00:19.0
  Hardware Class: network
  Model: "Intel 82567LF-2 Gigabit Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x10cd "82567LF-2 Gigabit Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x5001 
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  Memory Range: 0xe3200000-0xe321ffff (rw,non-prefetchable)
  Memory Range: 0xe3224000-0xe3224fff (rw,non-prefetchable)
  I/O Ports: 0xf100-0xf11f (rw)
  IRQ: 26 (1037426 events)
  HW Address: 00:27:0e:01:b2:89
  Link detected: yes
  Module Alias: "pci:v00008086d000010CDsv00008086sd00005001bc02sc00i00"
  Driver Info #0:
    Driver Status: e1000e is active
    Driver Activation Cmd: "modprobe e1000e"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 203.0: 0282 WLAN controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_168c_1a
  Unique ID: y9sn.xZ3s5UAJ139
  Parent ID: 6NW+.rH3rArjV8aF
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:03.0
  SysFS BusID: 0000:02:03.0
  Hardware Class: network
  Model: "Atheros AR2413 802.11bg NIC"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x001a "AR2413 802.11bg NIC"
  SubVendor: pci 0x1186 "D-Link System Inc"
  SubDevice: pci 0x3a1d 
  Revision: 0x01
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xe3100000-0xe310ffff (rw,non-prefetchable)
  IRQ: 21 (653823 events)
  HW Address: 00:24:01:11:e5:e1
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000001Asv00001186sd00003A1Dbc02sc00i00"
  Driver Info #0:
    Driver Status: ath5k is active
    Driver Activation Cmd: "modprobe ath5k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (PCI bridge)
cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory
Module                  Size  Used by
xt_TCPMSS               4640  1 
xt_limit                3236  14 
xt_tcpudp               3616  13 
nf_nat_irc              2688  0 
nf_nat_ftp              3584  0 
ipt_LOG                 6404  8 
ipt_MASQUERADE          2944  1 
xt_DSCP                 3744  0 
ipt_REJECT              3584  1 
nf_conntrack_irc        6552  1 nf_nat_irc
nf_conntrack_ftp        8984  1 nf_nat_ftp
xt_state                2432  8 
binfmt_misc            10220  1 
dm_crypt               14888  0 
arc4                    2144  2 
ecb                     3296  2 
ath5k                 137352  0 
mac80211              210040  1 ath5k
led_class               5256  1 ath5k
ath                    10304  1 ath5k
snd_hda_codec_idt      73008  1 
iptable_nat             6656  1 
nf_nat                 22452  4 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      16376  11 iptable_nat,nf_nat
nf_conntrack           80800  9 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
iptable_mangle          4192  0 
snd_hda_intel          31976  4 
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9384  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
iptable_filter          3872  1 
joydev                 13088  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ip_tables              21200  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               25832  10 xt_TCPMSS,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
cfg80211              109144  3 ath5k,mac80211,ath
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                58020  0 
snd                    77192  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
serio_raw               6596  0 
nvidia              10316904  26 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  1 lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
usbhid                 43968  0 
e1000e                138544  0 
intel_agp              33264  0 



```


Edit: I am no longer using Firestarter.  I have gufw installed but currently de-activated.

---

### Post by watchpocket on 2010-11-14
A bit more info:

```

517 --> ifconfig -a                          
eth0      Link encap:Ethernet  HWaddr 00:27:0e:01:b2:89  
          inet addr:67.81.187.226  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::227:eff:fe01:b289/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:884224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:518358151 (518.3 MB)  TX bytes:22352645 (22.3 MB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4199 (4.1 KB)  TX bytes:4199 (4.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:11:e5:e1  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:fe11:e5e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6510 (6.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-11-E5-E1-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

518 --> route -n       
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
67.81.176.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         67.81.176.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0


```lspci:

```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
02:00.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```lsusb:

```

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0488:00df Cirque Corp. 
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```.

---

### Post by watchpocket on 2010-11-15
.

---

