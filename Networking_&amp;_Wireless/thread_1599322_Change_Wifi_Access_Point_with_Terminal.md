---
title: "Change Wifi Access Point with Terminal"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by heyandy889 on 2010-10-17
Hello. :D

I am sitting on my campus. Here, we have wireless internet throughout campus. I was with a friend, once, who changed the wifi access point he used. Right now, the internet is pretty slow, so I was wondering if maybe I could change to a different access point to help.

I found the command "sudo iwlist scan" on the Ubuntu forums, here is my output from that.

```
nate@nate-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:40:96:5A:17:B7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000011e0a06aeb1d
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 851E000086001F00FF0019004263632D312D30322D53747277792D000A000006
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890006850000228500004164BC0061736600
          Cell 02 - Address: 00:12:00:25:58:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000011e0ad091b1c
                    Extra: Last beacon: 2808ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000084000F00FF0319004263632D322D30312D42616C526D2D0008000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:07:85:B3:DC:6B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000007b39138c930
                    Extra: Last beacon: 2740ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 851E000084001F00FF0019004263632D302D30312D4D63442D30310012000007
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890002850000238500004264BC0062736600
          Cell 04 - Address: D2:15:9D:AE:EB:74
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000018c847cf666
                    Extra: Last beacon: 2540ms ago
sunami                     IE: Unknown: 000768707365747570
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: DD09001018020000000000
          Cell 05 - Address: 00:0B:FD:AC:91:40
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:6 Mb/s; 9 Mb/s
                    Mode:Master
                    Extra:tsf=000007b394e70615
                    Extra: Last beacon: 2220ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 01028C12
                    IE: Unknown: 851E000084001F00FF0019004263632D302D30312D4D63442D30310003000023
                    IE: Unknown: 9606004096001000
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F20201018900028500002385000042645E0062732F00
          Cell 06 - Address: 00:1C:91:02:15:B4
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000000ea17bc113
                    Extra: Last beacon: 2364ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
sunami                     IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000007127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 07 - Address: 00:40:96:49:5A:2D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000011e0a797128d
                    Extra: Last beacon: 2580ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 851E000086001F00FF0019004263632D312D30382D3130362D30360004000006
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890006850000228500004164BC0061736600
          Cell 08 - Address: 00:40:96:49:5A:63
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"tsunami"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000011e0a4ccab46
                    Extra: Last beacon: 2952ms ago
                    IE: Unknown: 00077473756E616D69
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 851E000086001F00FF0019004263632D312D30332D4D61696E4F660001000006
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890006850000228500004164BC0061736600

```I assume that each of the "Cell"s are Wifi access points to which I can connect? Would connecting to a different Cell give me faster internet?

Thanks,
heyandy889

---

