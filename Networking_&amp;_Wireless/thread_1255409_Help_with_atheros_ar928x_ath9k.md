---
title: "Help with atheros ar928x ath9k"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2009-09-01
Hey guys,

I know there are a couple posts about this already, but the solutions for the other guys don't seem to be working for me.  Right now, I am using linux-backports to get the card to work.  It works off and on.  I stopped using network manager because it dropped the signal like every 5 minutes.  Wicd works better but still drops the signal.  Its weird, if I hit refresh on Wicd, it will sometimes jump start it and the signal will reconnect other times nothing will work.  I also do sudo modprobe -r ath9k the sudo modprobe ath9k.  And SOMETIMES that will work to get it to reconnect.  Other times, nothing works, restart, poweroff, etc.

I tried loading up compat-wirless first, but that didn't work at all so I gave up on that.

Thanks!

Also, I am using jaunty 64bit.
  2.6.28-15-generic x86_64


Here are some outputs:
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
0c:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)



sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:a8:8a:50
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.7-7 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:b6:c3:67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=154.32.1.3 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn


sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:3E:F8:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"The Lows"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035d175c99c
                    Extra: Last beacon: 3788ms ago
                    IE: Unknown: 0008546865204C6F7773
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6E1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD730050F204104A0001101044000102103B000103104700101E2556EFFA8C98343B39AB86004C14E5102100074E45544745415210230007574E523335303010240007574E52333530301042000A313233343536373839301054000800060050F204000110110007574E5233353030100800020086
          Cell 02 - Address: 00:22:6B:9B:9F:37
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ee513fc7d
                    Extra: Last beacon: 3736ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050100000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A88000226B9B9F371021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
          Cell 03 - Address: 00:22:A4:09:CD:21
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"2WIRE442"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ee0b6b181
                    Extra: Last beacon: 3528ms ago
                    IE: Unknown: 00083257495245343432
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 00:22:A4:6D:CE:59
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"HOME133"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f3fec3d12d
                    Extra: Last beacon: 3404ms ago
                    IE: Unknown: 0007484F4D45313333
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 00:1C:10:04:87:B1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ee6d187b1
                    Extra: Last beacon: 3468ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 06 - Address: 00:14:A5:90:0E:7F
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"wireless#1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ee4e50232
                    Extra: Last beacon: 3232ms ago
                    IE: Unknown: 000A776972656C6573732331
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010180100
          Cell 07 - Address: 00:1D:7E:93:F4:EB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"@HomeF4EB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e9faa64b14
                    Extra: Last beacon: 3148ms ago
                    IE: Unknown: 000940486F6D6546344542
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4301000000
          Cell 08 - Address: 00:24:56:6A:77:31
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"2WIRE001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000186c28d5181
                    Extra: Last beacon: 3736ms ago
                    IE: Unknown: 00083257495245303031
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 09 - Address: 00:1D:5A:7E:3D:E1
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"2WIRE554"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011531446181
                    Extra: Last beacon: 3552ms ago
                    IE: Unknown: 00083257495245353534
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 10 - Address: 00:22:A4:02:B2:21
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"2WIRE413"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031dc208bb3c
                    Extra: Last beacon: 3724ms ago
                    IE: Unknown: 00083257495245343133
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 11 - Address: 00:22:A4:00:82:71
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=8/70  Signal level=-102 dBm  
                    Encryption key:on
                    ESSID:"2WIRE995"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a3a5c0181
                    Extra: Last beacon: 3276ms ago
                    IE: Unknown: 00083257495245393935
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 12 - Address: 00:21:29:73:71:B9
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Maile's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009720002183
                    Extra: Last beacon: 3284ms ago
                    IE: Unknown: 000F4D61696C652773204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 13 - Address: 00:22:3F:90:E7:E7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=4/70  Signal level=-106 dBm  
                    Encryption key:on
                    ESSID:"smittyjo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000100bce7180
                    Extra: Last beacon: 3804ms ago
                    IE: Unknown: 0008736D697474796A6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
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
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001900000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD2C0050F204104A0001101044000101105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000103
          Cell 14 - Address: 00:1D:5A:D8:D4:21
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=6/70  Signal level=-104 dBm  
                    Encryption key:on
                    ESSID:"2WIRE105"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d2ca64181
                    Extra: Last beacon: 3752ms ago
                    IE: Unknown: 00083257495245313035
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
          Cell 15 - Address: 00:24:56:62:C6:69
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=7/70  Signal level=-103 dBm  
                    Encryption key:on
                    ESSID:"2WIRE585"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001893e370181
                    Extra: Last beacon: 3640ms ago
                    IE: Unknown: 00083257495245353835
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 16 - Address: 00:22:A4:03:27:F1
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"2WIRE298"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000a41181
                    Extra: Last beacon: 3608ms ago
                    IE: Unknown: 00083257495245323938
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 17 - Address: 00:14:95:AF:1B:B1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=5/70  Signal level=-105 dBm  
                    Encryption key:on
                    ESSID:"PBCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000152320b331
                    Extra: Last beacon: 3336ms ago
                    IE: Unknown: 000450424343
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010100
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C



dmesg | grep -e ath -e wlan
[    3.489259] device-mapper: multipath: version 1.0.5 loaded
[    3.489261] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.734401] ath9k 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.734431] ath9k 0000:0c:00.0: setting latency timer to 64
[   10.169649] WARNING: at /build/buildd/linux-backports-modules-2.6.28-2.6.28/debian/build/build-generic/compat-wireless-2.6/drivers/net/wireless/ath9k/regd.c:151 ath9k_world_regdomain+0x28/0x90 [ath9k]()
[   10.169651] Modules linked in: ath9k(+) lbm_cw_mac80211 led_class lbm_cw_cfg80211 ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[   10.169668]  [<ffffffff80250b6f>] warn_on_slowpath+0x5f/0x90
[   10.169681]  [<ffffffffa00ffd58>] ath9k_world_regdomain+0x28/0x90 [ath9k]
[   10.169687]  [<ffffffffa0104975>] ath_attach+0x5f5/0xb90 [ath9k]
[   10.169693]  [<ffffffffa010c5cc>] ath_pci_probe+0x16c/0x320 [ath9k]
[   10.169725]  [<ffffffffa012d000>] ? ath9k_init+0x0/0x57 [ath9k]
[   10.169732]  [<ffffffffa012d000>] ? ath9k_init+0x0/0x57 [ath9k]
[   10.169738]  [<ffffffffa012d000>] ? ath9k_init+0x0/0x57 [ath9k]
[   10.169743]  [<ffffffffa010c79e>] ath_pci_init+0x1e/0x20 [ath9k]
[   10.169748]  [<ffffffffa012d019>] ath9k_init+0x19/0x57 [ath9k]
[   10.169771]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[   10.170234] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.945081] Registered led device: ath9k-phy0::radio
[   10.945111] Registered led device: ath9k-phy0::assoc
[   10.945141] Registered led device: ath9k-phy0::tx
[   10.945168] Registered led device: ath9k-phy0::rx
[   17.110695] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.554614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.324123] wlan0: authenticate with AP ffff88007a985ac0
[   24.326264] wlan0: authenticated
[   24.326268] wlan0: associate with AP ffff88007a985ac0
[   24.329807] wlan0: RX AssocResp from ffff88007b5d604a (capab=0x411 status=0 aid=2)
[   24.329811] wlan0: associated
[   24.339276] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.338400] wlan0: authenticate with AP ffff88007a985ac0
[   28.340400] wlan0: authenticated
[   28.340402] wlan0: associate with AP ffff88007a985ac0
[   28.344430] wlan0: RX ReassocResp from ffff88007b10a04a (capab=0x411 status=0 aid=2)
[   28.344433] wlan0: associated
[   35.128041] wlan0: no IPv6 routers present
[   38.358647] wlan0: disassociating by local choice (reason=3)
[   42.259737] wlan0: authenticate with AP ffff88007a985ac0
[   42.261747] wlan0: authenticated
[   42.261749] wlan0: associate with AP ffff88007a985ac0
[   42.265272] wlan0: RX ReassocResp from ffff88007bd2e04a (capab=0x411 status=0 aid=2)
[   42.265274] wlan0: associated
[   52.290373] wlan0: disassociating by local choice (reason=3)
[   56.191736] wlan0: authenticate with AP ffff88007a985ac0
[   56.194201] wlan0: authenticated
[   56.194209] wlan0: associate with AP ffff88007a985ac0
[   56.201243] wlan0: RX ReassocResp from ffff88007b45e04a (capab=0x411 status=0 aid=2)
[   56.201247] wlan0: associated
[   66.216272] wlan0: disassociating by local choice (reason=3)
[   70.119750] wlan0: direct probe to AP ffff88007a985ac0 try 1
[   70.123877] wlan0 direct probe responded
[   70.123879] wlan0: authenticate with AP ffff88007a985ac0
[   70.126203] wlan0: authenticated
[   70.126206] wlan0: associate with AP ffff88007a985ac0
[   70.129694] wlan0: RX ReassocResp from ffff88007b06e04a (capab=0x411 status=0 aid=2)
[   70.129697] wlan0: associated
[   77.076074] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[   77.261055] wlan0: deauthenticating by local choice (reason=3)
[   77.401663] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.530645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.403199] wlan0: authenticate with AP ffff88007a985ac0
[   81.403236] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   81.406167] wlan0: authenticated
[   81.406174] wlan0: associate with AP ffff88007a985ac0
[   81.406186] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   81.600277] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   82.612932] wlan0: authenticate with AP ffff88007a985ac0
[   82.625644] wlan0: authenticate with AP ffff88007a985ac0
[   82.627956] wlan0: authenticated
[   82.627962] wlan0: associate with AP ffff88007a985ac0
[   82.632023] wlan0: RX AssocResp from ffff88007b10604a (capab=0x411 status=0 aid=2)
[   82.632030] wlan0: associated
[   82.642812] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   92.645342] wlan0: disassociating by local choice (reason=3)
[   93.560025] wlan0: no IPv6 routers present
[   96.559906] wlan0: authenticate with AP ffff88007a985ac0
[   96.562009] wlan0: authenticated
[   96.562015] wlan0: associate with AP ffff88007a985ac0
[   96.568076] wlan0: RX ReassocResp from ffff88007bd0e04a (capab=0x411 status=0 aid=2)
[   96.568083] wlan0: associated
[  126.624849] wlan0: deauthenticated (Reason: 2)
[  127.621062] wlan0: direct probe to AP ffff88007a985ac0 try 1
[  127.626025] wlan0 direct probe responded
[  127.626032] wlan0: authenticate with AP ffff88007a985ac0
[  127.628054] wlan0: authenticated
[  127.628059] wlan0: associate with AP ffff88007a985ac0
[  127.631681] wlan0: RX ReassocResp from ffff8800731cc04a (capab=0x411 status=0 aid=2)
[  127.631686] wlan0: associated
[  131.515021] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[  137.651461] wlan0: disassociating by local choice (reason=3)
[  141.556620] wlan0: authenticate with AP ffff88007a985ac0
[  141.558758] wlan0: authenticated
[  141.558764] wlan0: associate with AP ffff88007a985ac0
[  141.562373] wlan0: RX ReassocResp from ffff88007b1fe04a (capab=0x411 status=0 aid=2)
[  141.562381] wlan0: associated
[  151.576506] wlan0: disassociating by local choice (reason=3)
[  155.483128] wlan0: authenticate with AP ffff88007a985ac0
[  155.502821] wlan0: authenticate with AP ffff88007a985ac0
[  155.507846] wlan0: authenticated
[  155.507853] wlan0: associate with AP ffff88007a985ac0
[  155.511481] wlan0: RX ReassocResp from ffff880064f3e04a (capab=0x411 status=0 aid=2)
[  155.511487] wlan0: associated
[  164.181070] wlan0: deauthenticating by local choice (reason=3)
[  164.240063] wlan0: deauthenticating by local choice (reason=3)
[  165.859600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  188.450766] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  192.483226] wlan0: authenticate with AP ffff88007a985ac0
[  192.486163] wlan0: authenticated
[  192.486169] wlan0: associate with AP ffff88007a985ac0
[  192.492762] wlan0: RX AssocResp from ffff8800705d804a (capab=0x411 status=0 aid=1)
[  192.492769] wlan0: associated
[  192.504132] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  202.510120] wlan0: disassociating by local choice (reason=3)
[  202.828031] wlan0: no IPv6 routers present
[  206.516633] wlan0: authenticate with AP ffff88007a985ac0
[  206.526761] wlan0: authenticate with AP ffff88007a985ac0
[  206.528873] wlan0: authenticated
[  206.528877] wlan0: associate with AP ffff88007a985ac0
[  206.532952] wlan0: RX ReassocResp from ffff88007a92e04a (capab=0x411 status=0 aid=1)
[  206.532958] wlan0: associated
[  216.545937] wlan0: disassociating by local choice (reason=3)
[  220.457066] wlan0: authenticate with AP ffff88007a985ac0
[  220.459322] wlan0: authenticated
[  220.459329] wlan0: associate with AP ffff88007a985ac0
[  220.462969] wlan0: RX ReassocResp from ffff88007b43004a (capab=0x411 status=0 aid=1)
[  220.462977] wlan0: associated
[  230.476401] wlan0: disassociating by local choice (reason=3)
[  234.380605] wlan0: authenticate with AP ffff88007a985ac0
[  234.382757] wlan0: authenticated
[  234.382762] wlan0: associate with AP ffff88007a985ac0
[  234.386421] wlan0: RX ReassocResp from ffff88006093c04a (capab=0x411 status=0 aid=1)
[  234.386427] wlan0: associated
[  239.106340] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[  239.409053] wlan0: deauthenticating by local choice (reason=3)
[  239.571831] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.758778] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  243.655208] wlan0: authenticate with AP ffff88007a985ac0
[  243.655243] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  243.657413] wlan0: authenticated
[  243.657419] wlan0: associate with AP ffff88007a985ac0
[  243.657427] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  243.852266] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  245.896768] wlan0: authenticate with AP ffff88007a985ac0
[  245.899124] wlan0: authenticated
[  245.899131] wlan0: associate with AP ffff88007a985ac0
[  245.902603] wlan0: RX AssocResp from ffff88007b5d404a (capab=0x411 status=0 aid=1)
[  245.902610] wlan0: associated
[  245.914212] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  256.372246] wlan0: no IPv6 routers present
[ 3912.196098] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 3970.912289] wlan0: deauthenticated (Reason: 2)
[ 3971.912062] wlan0: direct probe to AP ffff88007a985ac0 try 1
[ 3972.112044] wlan0: direct probe to AP ffff88007a985ac0 try 2
[ 3972.116502] wlan0 direct probe responded
[ 3972.116511] wlan0: authenticate with AP ffff88007a985ac0
[ 3972.119889] wlan0: authenticated
[ 3972.119894] wlan0: associate with AP ffff88007a985ac0
[ 3972.133384] wlan0: RX ReassocResp from ffff8800681ac04a (capab=0x411 status=0 aid=1)
[ 3972.133392] wlan0: associated
[ 3976.017822] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 3988.515764] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 3992.148982] wlan0: disassociating by local choice (reason=3)
[ 3993.354610] wlan0: authenticate with AP ffff88007a985ac0
[ 3993.365614] wlan0: authenticate with AP ffff88007a985ac0
[ 3993.365876] wlan0: authenticated
[ 3993.365880] wlan0: associate with AP ffff88007a985ac0
[ 3993.371739] wlan0: RX ReassocResp from ffff88007bd1604a (capab=0x411 status=0 aid=1)
[ 3993.371746] wlan0: associated
[ 4066.149777] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4070.857779] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4079.233152] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4135.995855] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4141.969098] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4187.324391] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4208.679001] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4214.350171] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4236.938062] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request
[ 4706.206359] wlan0: beacon loss from AP ffff88007a985ac0 - sending probe request

---

### Post by bkratz on 2009-09-01
[QUOTE=ssc351;7881414]Hey guys,

I know there are a couple posts about this already, but the solutions for the other guys don't seem to be working for me.  Right now, I am using linux-backports to get the card to work.  It works off and on.  I stopped using network manager because it dropped the signal like every 5 minutes.  Wicd works better but still drops the signal.  Its weird, if I hit refresh on Wicd, it will sometimes jump start it and the signal will reconnect other times nothing will work.  I also do sudo modprobe -r ath9k the sudo modprobe ath9k.  And SOMETIMES that will work to get it to reconnect.  Other times, nothing works, restart, poweroff, etc.


It seems that you detect a lot of wireless networks, but only on certain channels.  If the desired one is the one on channel 1 it has competition with another at about the same strength signal.  You may want to change channels on your router.

---

### Post by ssc351 on 2009-09-01
I tried changing channels but it didn't help...I am pretty sure the problem lies within the computer...on Wicd, when it drops the signal, it I click refresh or do and iwlist scan...no networks show up

---

### Post by ssc351 on 2009-09-04
Help??? Anyone???

---

### Post by opennomad on 2009-10-14
Well, I've been struggling with this as well on my eee pc 1000HE, which uses the ath9k driver.  It seems that there is hope in the future.  I found the following developer thread, which suggests it might get better with kernel 2.6.30 and 2.6.31.

[http://lkml.indiana.edu/hypermail/linux/kernel/0904.0/03343.html](http://lkml.indiana.edu/hypermail/linux/kernel/0904.0/03343.html)

on my eeepc I have it setup to unload the driver and reload it based on the eeepc-utilities and hotkeys.  It makes things tolerable for now.

---

