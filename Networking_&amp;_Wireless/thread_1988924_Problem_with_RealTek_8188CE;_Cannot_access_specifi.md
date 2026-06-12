---
title: "Problem with RealTek 8188CE; Cannot access specific network"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by Durn Whippersnapper on 2012-05-28
My wireless card has worked in the past, but I just moved into a new apartment, and it won't work with the current network. Here's a few diagnostic outputs:

lspci
```

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176]
        Kernel driver in use: rtl8192ce
        Kernel modules: rtl8192cee

```

iwconfig
```

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"FENNO"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:8E:FE:1F   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.

```

lsmod | grep rtl
```

rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211

```

uname -a
```

Linux awelkie1-desktop 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

I can access the wireless network from my windows partition and also from my other linux machine. The network is using WPA 2 encryption. Any help would be appreciated.

---

### Post by praseodym on 2012-05-28
Please show:
```

iwconfig
rfkill list
iwlist chan
sudo iwlist scan
dmesg | grep rtl8
```

---

### Post by Durn Whippersnapper on 2012-05-28
rfkill list
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

iwlist chan
```

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
eth0      no frequency information.

```

iwlist scan
```

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 10:9A:DD:80:C7:29
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"I.K. Time Capsule"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000587a2374d7c
                    Extra: Last beacon: 664ms ago
                    IE: Unknown: 0011492E4B2E2054696D652043617073756C65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106109ADD80C729
          Cell 02 - Address: 00:1E:E5:78:13:AD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Neko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005414e5b164
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 00044E656B6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483351333935381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180203F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:22:3F:B9:99:8C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"chn6060"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005941f07e3d
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 000763686E36303630
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B0001031047001009582AF03D058176305D5F8AAC6AF74A1021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:26:F3:FD:9B:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"HOME-9B48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000232320117e5
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009484F4D452D39423438
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010024127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8800026F3FD9B481021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 05 - Address: 00:26:F3:FD:9B:49
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023231ff4bdf
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010024127A
                    IE: Unknown: DD07000C4300000000
          Cell 06 - Address: 00:26:F3:FD:9B:4B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002323200ecdd
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010024127A
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: 00:26:F2:8E:FE:1F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FENNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013536e1804
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000546454E4E4F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B071B00000000000000000000000000000000000000
                    IE: Unknown: 3D160B071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000026F28EFE1F1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 08 - Address: 00:26:F3:FD:9B:4A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002323200e3db
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010024127A
                    IE: Unknown: DD07000C4300000000

eth0      Interface doesn't support scanning.

```

dmesg | grep rtl8
```

[   16.382362] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.382372] rtl8192ce 0000:08:00.0: setting latency timer to 64
[   21.007241] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   21.503134] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   40.924118] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   51.419290] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   58.203816] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   62.434998] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   66.635095] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   70.866780] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   75.067362] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   79.266595] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   83.495739] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  192.195492] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  222.195070] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  262.192114] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  312.192233] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  365.628021] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  372.189266] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  432.189753] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  465.199416] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  469.404604] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  473.629718] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  477.824389] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  482.050951] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  488.724732] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  490.058461] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  494.255965] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  498.461664] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  502.663727] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  506.879634] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  511.077293] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin

```

---

### Post by praseodym on 2012-05-28
Change the encryption mode to pure WPA2-AES if possible.

---

### Post by gordintoronto on 2012-05-28
What version of Ubuntu? At some point in the past, Network Manager would not log on to a router whose SSID began with an upper-case letter.

---

### Post by Durn Whippersnapper on 2012-05-28
The machine that cannot access the network is running 12.04. The machine that can access the network is running 11.10. Was there an update in between these versions that makes the network manager not able to access the capitalized SSID?

---

### Post by Durn Whippersnapper on 2012-05-28
I was just able to access the network, for about 20 minutes, then I was disconnected and now I'm not able to connect again. So I guess I'm technically able to access the network, but for some reason I can't do it that often. However, my other machine has no such trouble. It might be my wireless card, but I thought the Realtek 8188CE was supported...

---

### Post by Durn Whippersnapper on 2012-05-28
I tried disabling ipv6 in network manager, but that didn't seem to help

---

