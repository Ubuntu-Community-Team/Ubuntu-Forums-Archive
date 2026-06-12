---
title: "Intel / 13.04 / Lenovo Y580 / Wireless &amp; Wired Connection Issue"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by KFwLsKvVAs on 2013-05-09
Greetings,

After upgrading to 13.04, I lost network connectivity (wired and wireless).  I fixed the wired issue, but now I cannot connect to my network through wifi.  I have posted below the information requested in the sticky.  

Also, to give a better description of the problem: the wlan0 interface appears to be up, but when I try to connect to my network the notification just says "Connecting..." and it stays like that until it stops connecting.  

Thanks in advance.  

EDIT: The wired problem is actually not fixed.  In fact, it's nigh unusable.  I am able to connect to my wired network, ping 8.8.8.8 or any other site, and get online in a browser.  After a few minutes however, even though I am still connected, I am unable to send/receive information (by pinging google's server or through a browser).  The issue is resolved by opening up a terminal and issuing the command

```

$ sudo modprobe -r alx && sudo modprobe alx

```

but that's really not a solution since it just breaks again after 10 or 15 minutes.  

I am posting this from my 12.10 partition.  I've included the lspci for the ethernet, if any other information is needed I would be glad to supply it.  

```

$ lspci | grep Ethernet
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)

```

```
$ lspci | grep Network
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)

```


```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:88:e3:81:2d:a9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba88:e3ff:fe81:2da9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:216887578 (216.8 MB)  TX bytes:6401721 (6.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97071 (97.0 KB)  TX bytes:97071 (97.0 KB)

wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:5c:1e:b0  
          inet6 addr: fe80::9e4e:36ff:fe5c:1eb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9289 (9.2 KB)  TX bytes:36025 (36.0 KB)

```



```

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"KFwLsKvVAs"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:77:7D:C1   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0

```




```

$ lsmod | grep wifi
iwlwifi               173477  1 iwldvm
cfg80211              510937  3 iwlwifi,mac80211,iwldvm

```




```

$ sudo lshw -C network
[sudo] password for bonez: 
  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 08
       serial: b8:88:e3:81:2d:a9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:d3600000-d363ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:5c:1e:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-19-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:d3500000-d3501fff

```


```

$ iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:77:7D:C1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"KFwLsKvVAs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000034a2cd69a01
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 000A4B46774C734B76564173
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 5E:FF:FA:FA:2A:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000050303d229b12
                    Extra: Last beacon: 21200ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020011000000
          Cell 03 - Address: 28:16:2E:D2:C2:61
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"2WIRE048"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000004b6b99
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 00083257495245303438
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030107
                    IE: Unknown: 0706555320010B1B
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
          Cell 04 - Address: 74:9D:DC:ED:D2:C1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"2WIRE421"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000c47e3e
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 00083257495245343231
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
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
          Cell 05 - Address: 20:10:7A:58:71:A6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"SBG6580DA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000336276918
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 0009534247363538304441
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 20:10:7A:7F:7E:E5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"SBG658012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d31a98a5
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 0009534247363538303132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100084D6F746F726F6C61102300084D6F746F726F6C611024000631323334353610420007303030303030311054000800060050F20400011011000A4D6F746F726F6C614150100800020088103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:0C:41:A0:5E:66
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b81087b95
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
          Cell 08 - Address: 20:4E:7F:31:34:C4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Poofy Doofus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002cb3e0cd80
                    Extra: Last beacon: 21392ms ago
                    IE: Unknown: 000C506F6F667920446F6F667573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403080A00000000000000000000000000000000000000
                    IE: Unknown: 3D1603080A00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000204E7F3134C4102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 09 - Address: 94:44:52:09:8D:9B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"j-wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001edba5d50bc
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 000A6A2D776972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B0001031047001000000000000000011000944452098D9B1021001242656C6B696E20436F72706F726174696F6E1023000C463544373233342D3420763510240007352E30302E31321042000E31323934353732333433313232361054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD050050F20500
          Cell 10 - Address: A0:21:B7:B5:6E:A4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"jkfendrick"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000223ba8aca0c
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 000A6A6B66656E647269636B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B000103104700106E108A9EC7AC57FF95FAA021B7B56EA5102100044E54475210230007574E52323030301024000256331042000C6130323162376235366561351054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020004103C0001011049000600372A000120
          Cell 11 - Address: 98:FC:11:85:FC:12
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Cisco08964"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004bd79f001cc
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 000A436973636F3038393634
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001011041000100103B00010310470010CB39953168107B597667DF1703A7A9A91021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 12 - Address: 00:16:B6:02:68:B5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"tknight"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b88cf0ef6
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 0007746B6E69676874
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD09001018020014000000
          Cell 13 - Address: 00:23:69:22:45:B9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"katiez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000972bcb1d672
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 00066B617469657A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 14 - Address: E4:11:5B:06:C0:67
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-67-Deskjet 3510 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000223bb673da5
                    Extra: Last beacon: 21128ms ago
                    IE: Unknown: 001F48502D5072696E742D36372D4465736B6A6574203335313020736572696573
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD740800090004000000070102010002017803134465736B6A6574203335313020736572696573040F33353132000000000000000F434E320510434E3235533132474A3930355237000006101C852A4DB8001F08ABCDE4115B06C0670704C0A80104080200C4090200080A04000000010B0400000000
          Cell 15 - Address: EC:1A:59:2F:C6:6E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"belkin.66e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023b2dd8b96
                    Extra: Last beacon: 20876ms ago
                    IE: Unknown: 000A62656C6B696E2E363665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202100C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B0001031047001000000000000000010003EC1A592FC66E1021001242656C6B696E20436F72706F726174696F6E1023000946394B31303031763410240007342E30302E30361042000E31323132333247423432383436321054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080

```


```

$ lsb_release -d
Description:	Ubuntu 13.04

```

```

$ uname -mr
3.8.0-19-generic x86_64

```

---

### Post by KFwLsKvVAs on 2013-05-10
Bump.  

Could anybody give me some place to start at least?  Would installing an earlier version of the driver help?

---

### Post by grahammechanical on 2013-05-10
Have you considered that the problem lies between the router and the ISP and not between the computer and the router? Those command listings that you provide show that the machine is connected to the router both by ethernet and wireless adapter. The drivers are installed and working. The wireless adapter is detecting wireless access points..

I have never had a problem on my machine with getting a connection to my router. So, to learn about the listings/reports I simulated a failure. Disable Wired Connections and run those commands again. Disable Wireless connections and run those commands again. Compare the reports. Notice the differences when things are broken and when they are working.

Go into the router set up program and see if there is any indication of a breakdown at the ISP. Check the connection to the ISP. Go online to the ISP's web site to see if there are reports of the ISP being down for repairs or something like that. Check the quality of the connection to the ISP. Is the telephone wiring of good quality?

Is there an alternative driver that can be used?

Regards

---

### Post by KFwLsKvVAs on 2013-05-10
I'm about 100% sure it's not a router or ISP problem.  On the same computer on a windows 8 partition and an ubuntu 12.10 partition everything works fine.

---

### Post by praseodym on 2013-05-10
First try to deactivate the N-mode of the wifi driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Second, please show

```
cat /etc/resolv.conf
route -n
dmesg | egrep 'alx|iwl'

```

---

### Post by KFwLsKvVAs on 2013-05-10
praseodym, thanks for your reply.  

I tried what you said.  

The output of the commands is as follows:

```

$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1

$ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.

$ sudo modprobe -v iwlwifi
$

```

And the output of the second set of commands is as follows:
```

$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search wi.rr.com

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

$ dmesg | egrep 'alx|iwl'
[   21.131420] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.275854] alx 0000:02:00.0: alx(b8:88:e3:81:2d:a9): Qualcomm Atheros Ethernet Network Connection
[   21.378144] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   21.392297] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   21.392300] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   21.392302] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   21.392303] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   21.392305] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   21.392307] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   21.392479] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   21.413298] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.632531] alx 0000:02:00.0: irq 47 for MSI/MSI-X
[   28.632537] alx 0000:02:00.0: irq 48 for MSI/MSI-X
[   28.632542] alx 0000:02:00.0: irq 49 for MSI/MSI-X
[   28.632546] alx 0000:02:00.0: irq 50 for MSI/MSI-X
[   28.632551] alx 0000:02:00.0: irq 51 for MSI/MSI-X
[   28.632555] alx 0000:02:00.0: irq 52 for MSI/MSI-X
[   28.632559] alx 0000:02:00.0: irq 53 for MSI/MSI-X
[   28.632563] alx 0000:02:00.0: irq 54 for MSI/MSI-X
[   28.632569] alx 0000:02:00.0: irq 55 for MSI/MSI-X
[   28.633815] alx 0000:02:00.0 eth0: NIC Link Up: 1 Gbps Full
[   28.638089] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   28.645651] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   29.011952] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   29.019469] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   34.758198] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   83.558702] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  133.489578] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  183.428215] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  258.956394] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  398.197059] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use

```

---

### Post by KFwLsKvVAs on 2013-05-10
In case it matters, my connection is WPA encrypted.  I have no problems connecting to it from my 12.10 partition or my win8 partition.

---

### Post by KFwLsKvVAs on 2013-05-10
grahammechanical,

I am fairly certain this is a driver issue.  From what I've read, you shouldn't use a driver version below what your kernel version is (from the compat-wireless page: 

"compat-wireless stable releases

Here are the list of stable releases of compat-wireless.

NOTE: Please be aware that the releases below contain code from the given version of the Linux kernel. Therefore to add functionality, you should select a version that is later than your kernel version.").  

The versions of the driver which I use are listed here: [http://wireless.kernel.org/en/users/Download/stable#compat-wireless_stable_releases](http://wireless.kernel.org/en/users/Download/stable#compat-wireless_stable_releases)

As you can see, the latest stable is for the 3.6 kernel, whereas the upgrade pushed me on to the 3.8 kernel.

---

### Post by praseodym on 2013-05-11
What about WPA2?

---

### Post by KFwLsKvVAs on 2013-05-14
What about it?  I can connect reliably on my ubuntu 12.10 partition.

---

### Post by KFwLsKvVAs on 2013-05-19
Bump?

---

### Post by KFwLsKvVAs on 2013-05-22
I could still use some help with this.  Or should I just install 12.10?  Will the Atheros drivers ever just be included by default?

---

### Post by praseodym on 2013-05-23
Please check now (again):
```

route -n
iwconfig
iwlist chan
sudo iwlist scan
ifconfig -a
```

---

