---
title: "Ubuntu 11.10 can't connect with wifi"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by karol4722 on 2011-12-09
Hey
I didn't use my computer for 4 days and when I returned yesterday I got a problem... I cant connect with my network. Ubuntu shows all networks but it can't connect with them. I dont know why. I have normal internet only while it's trying to connect and when I type
```
/etc/init.d/networking restart
```
it shows:
```
root@muhahaha:/home/karol# /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Plugin rp-pppoe.so loaded.
PPP session is 45
Connected to 00:0c:42:b1:24:ca via interface wlan0
Using interface ppp0
Connect: ppp0 <--> wlan0
CHAP authentication succeeded
peer from calling number 00:0C:42:B1:24:CA authorized
local  IP address 82.160.78.217
remote IP address 10.0.0.2
primary   DNS address 10.0.0.2
                                                                         [ OK ]

```
Its 1 - 2 mins. I have windows on other partition too and everything is good there. What should I do?
I tried with wicd but it cant connect too
sorry for my english

EDIT:
```

root@muhahaha:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0E:8E:1A:1B:7D
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"AK_ZG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000010dca04536
                    Extra: Last beacon: 488ms ago
                    IE: Unknown: 0005414B5F5A47
                    IE: Unknown: 010482040B16
                    IE: Unknown: 03010A
                    IE: Unknown: DD2A000C42000000011E0000000033660902FF0F303030453845314131423744000000000000000005029909
          Cell 02 - Address: 00:22:75:E0:93:A8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ERYKBIALOWAS-HP_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001eba852069
                    Extra: Last beacon: 1084ms ago
                    IE: Unknown: 00174552594B4249414C4F5741532D48505F4E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
                    IE: Unknown: DDB70050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F002275E093A81021001442656C6B696E20496E7465726E6174696F6E616C10230018456E68616E63656420576972656C65737320526F757465721024000C463644343233302D342076311042000E32303934323432333031303938341054000800060050F20400011011001F42656C6B696E20456E68616E63656420576972656C65737320526F75746572100800020084103C000101
          Cell 03 - Address: 00:1D:0F:D1:1A:D2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"zp13-5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000040e09e9a6
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 00067A7031332D35
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706534120010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000001D0FD11AD2021D0FD11AD264002C010808
          Cell 04 - Address: 00:4F:62:1F:CD:80
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"kaska"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ca3e181b0
                    Extra: Last beacon: 708ms ago
                    IE: Unknown: 00056B61736B61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: Unknown: 050400010000
          Cell 05 - Address: 00:4F:62:15:D2:11
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"house1310"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ca379726c
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 0009686F75736531333130
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
          Cell 06 - Address: 00:4F:62:16:C9:9F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ZG22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ca1cb21b1
                    Extra: Last beacon: 6088ms ago
                    IE: Unknown: 00045A473232
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK



```
is something wrong with this?

---

