---
title: "Wireless only starts working once wired is plugged in"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by mattmattmatt on 2012-07-26
So here is the complete story:

I've installed Ubuntu Server onto my new Sony VAIO T Series laptop for a skeleton ubuntu install. Then I installed ubuntu-desktop with --no-install-recommends so that I could have a very basic ubuntu desktop setup. Everything worked great, ethernet was fine but when I tried to setup wireless it seemed to work until I restarted the computer.

After the restart wifi stopped working and no network indicator was present at the top. I plugged in the wired connection and boom, wireless was back!?

I'm not sure whats going on here but each restart seems to be disabling the wireless network. I'm fairly new to Linux/Ubuntu and so I'm not sure how to fix this.

Here is what I get when I restart the computer running the following commands **(i.e. no wireless)**:
```

lshw -C Network
iwlist scan
dmesg | grep -e iwl -e eth

```

```

mihok@MIHOK-VAIO:~$ sudo lshw -C Network
[sudo] password for mihok: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 84:4b:f5:c9:47:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c3000000-c307ffff memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 07
       serial: 30:f9:ed:fe:e8:51
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff
mihok@MIHOK-VAIO:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

mihok@MIHOK-VAIO:~$ sudo dmesg | grep -e iwl -e eth
[    0.731627] i2c-core: driver [aat2870] using legacy suspend method
[    0.731629] i2c-core: driver [aat2870] using legacy resume method
[    1.496522] r8169 0000:0e:00.0: eth0: RTL8168evl/8111evl at 0xffffc9000063e000, 30:f9:ed:fe:e8:51, XID 0c900800 IRQ 42
[    1.496525] r8169 0000:0e:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   17.789360] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.185803] r8169 0000:0e:00.0: eth0: link down
[   18.186046] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Here is the same commands, once I've plugged in the ethernet **(i.e. wireless works)**:
```

mihok@MIHOK-VAIO:~$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 84:4b:f5:c9:47:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic firmware=N/A ip=192.168.1.113 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c3000000-c307ffff memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 07
       serial: 30:f9:ed:fe:e8:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.1.114 latency=0 multicast=yes
       resources: irq:42 ioport:2000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff
mihok@MIHOK-VAIO:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:FB:EF:D4
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MIHOK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000109c86cbf
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 00054D49484F4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001B00000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F74FBEFD4102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30351042000C4A555430304B4239303539381054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
          Cell 02 - Address: C0:C1:C0:4E:95:69
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"YM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b4eaa5e7199
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 0002594D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001034738BFAAD15A520A8088A3C8450850F1021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1C:F0:56:15:3D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Arns"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e7f9e181
                    Extra: Last beacon: 916ms ago
                    IE: Unknown: 000441726E73
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010006FF7F
                    IE: Unknown: DD0C00037F020101000002A34000
          Cell 04 - Address: 74:EA:3A:F5:60:C8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Joetian"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001173a2721d
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 00074A6F657469616E
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
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051900000000000000000000000000000000000000
                    IE: Unknown: 3D1601051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000102103B000103104700100000000000001000000074EA3AF560C81021000754502D4C494E4B10230009544C2D57523834314E10240007362E302F372E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
          Cell 05 - Address: 00:19:E3:FB:62:D8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"CanuckN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000022c96ed3785
                    Extra: Last beacon: 13428ms ago
                    IE: Unknown: 000743616E75636B4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301680320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F207000101060019E3FB62D8
          Cell 06 - Address: 00:13:46:F7:88:7A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"thisaintfree"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000cd91181
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 000C7468697361696E7466726565
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 07 - Address: 30:46:9A:FE:4A:14
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000062698ed80
                    Extra: Last beacon: 12832ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001900000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A0001101044000102104700100000000000001000000030469AFE4A14103C000103
          Cell 08 - Address: 00:13:10:91:04:D6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"meuwemedia1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a05ea18d
                    Extra: Last beacon: 12824ms ago
                    IE: Unknown: 000B6D657577656D6564696131
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020205
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 78:CA:39:42:10:DF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Brent Herfindahl's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d21a4a4181
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 001A4272656E742048657266696E6461686C2773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B12
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120
          Cell 10 - Address: 00:22:2D:DE:54:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"christinajulie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f7afd227
                    Extra: Last beacon: 12056ms ago
                    IE: Unknown: 000E636872697374696E616A756C6965
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000015127A
                    IE: Unknown: DD07000C4304000000
          Cell 11 - Address: 00:22:2D:DE:54:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f7afd888
                    Extra: Last beacon: 12056ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000015127A
                    IE: Unknown: DD07000C4304000000
          Cell 12 - Address: 84:C9:B2:50:B7:F3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"i dont know"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024ada2dd80
                    Extra: Last beacon: 12016ms ago
                    IE: Unknown: 000B6920646F6E74206B6E6F77
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010020
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B00000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD270050F204104A0001101044000102104700100000000000001000000084C9B250B7F3103C000103

eth0      Interface doesn't support scanning.

mihok@MIHOK-VAIO:~$ sudo dmesg | grep -e iwl -e eth
[    0.731627] i2c-core: driver [aat2870] using legacy suspend method
[    0.731629] i2c-core: driver [aat2870] using legacy resume method
[    1.496522] r8169 0000:0e:00.0: eth0: RTL8168evl/8111evl at 0xffffc9000063e000, 30:f9:ed:fe:e8:51, XID 0c900800 IRQ 42
[    1.496525] r8169 0000:0e:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   17.789360] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.185803] r8169 0000:0e:00.0: eth0: link down
[   18.186046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  270.056860] r8169 0000:0e:00.0: eth0: link up
[  270.057662] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  280.769878] eth0: no IPv6 routers present
[  291.182622] r8169 0000:0e:00.0: eth0: link down

```

---

### Post by mattmattmatt on 2012-07-26
Something else I've noticed, when I disconnect from a wireless connection, and call ifconfig from the terminal, this is what is returned:

```

eth0      Link encap:Ethernet  HWaddr 30:f9:ed:fe:e8:51  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::32f9:edff:fefe:e851/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11778 (11.7 KB)  TX bytes:9596 (9.5 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:267715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13416410 (13.4 MB)  TX bytes:13416410 (13.4 MB)

wlan0     Link encap:Ethernet  HWaddr 84:4b:f5:c9:47:45  
          inet6 addr: fe80::864b:f5ff:fec9:4745/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:748348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086692384 (1.0 GB)  TX bytes:33869867 (33.8 MB)


```

Why would the ethernet still have an IP? Its not connected, and the wifi has been disconntected??

---

### Post by Cheesehead on 2012-07-26
Did your Ubuntu-desktop install include Network Manager?

Also, please paste the contents of the following files here:
/etc/network/interfaces
/etc/udev/rules.d/70-persistent-net.rules

---

### Post by mattmattmatt on 2012-07-26
I had read several google search results and tried installing network-manager and network-manager-gnome to realize that It wasnt event enabled (wireless) to which I did some more google searches and found the rfkill list all to confirm that there was a soft-block on it. I used rfkill unblock all to fix this.

Heres /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

And here is /etc/udev/rules.d/70-persistent-net.rules

```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="30:f9:ed:fe:e8:51", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="84:4b:f5:c9:47:45", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

Thanks so much for the help

---

### Post by Cheesehead on 2012-07-27
Here is the problem: You have set up two conflicting networking systems, and one is misconfigured.

Fix it by removing the bold instructions from  /etc/network/interfaces.
When using Network Manager, usually only the loopback interface should be defined in /etc/network/interfaces.

> **mattmattmatt said:**
> 
Heres /etc/network/interfaces

```

...

[B]# The primary network interface
auto eth0
iface eth0 inet dhcp[/B]

```


Then reboot to reload networking properly. Real reboot, not just logout.

---

### Post by mattmattmatt on 2012-07-27
You sir, are a gentleman and a scholar! Thank you so much, that did it. Instantly finds the wireless network and boots faster too!

---

