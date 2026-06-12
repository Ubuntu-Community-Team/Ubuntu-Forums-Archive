---
title: "Cannot connect to specific wireless network with ubuntu 12.04"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by YJLWPBD on 2013-08-30
I am using ubuntu 12.04 for 2 years now and I have encountered this problem about 2 months ago. Before I was able to connect to my home wifi without a problem (I have a windows pc and another ubuntu 12.04 laptop with which I can connect troublefree). I own an old Medion laptop with an Atheros AR5007UG chipset. I read multiple threads with similar problems and I tried several methods to solve this issue, like using Wicd network manager but nothing worked. As stated in the title, I can connect to different networks just fine. Granted, within the 2 months it connected like 3-5 times completely randomly. I tried reinstalling the drivers etc and another linux OS but I always had the same problem. Since my laptop is quite old and runs pretty slow I would very much like to keep linux on it and I would very much appreciate any help with this. I am sorry for any repitition from a similar thread but I feel like I need to post this seperately to fix it.

---

### Post by praseodym on 2013-08-31
Please show
```

lspci -nnk | grep -iA2 net
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by YJLWPBD on 2013-08-31
First of all thanks for the quick reply man. Here's the output of all the commands whereby my home wifi and the one in question would be the last one in cell 05:

```

sam@sam-WIM2120:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Wistron Corp. Device [17c0:1053]
    Kernel driver in use: r8169
sam@sam-WIM2120:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


sam@sam-WIM2120:~$ iwlist chan
lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
eth0      no frequency information.

sam@sam-WIM2120:~$ sudo iwlist scan
lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:8E:F2:63:EC:B0
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/100  Signal level=23/100  
                    Encryption key:on
                    ESSID:"NETGEAR13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005e5fbcc4d80
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 00094E4554474541523133
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD760050F204104A0001101044000102103B0001031047001000000000000010000000008EF263ECB0102100044E54475210230007574E5232323030102400016E104200046E6F6E651054000800060050F204000110110014574E523232303028576972656C65737320415029100800020086103C000103
          Cell 02 - Address: 00:24:01:D5:68:CE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/100  Signal level=14/100  
                    Encryption key:on
                    ESSID:"Kanzlei"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012b0c5db235
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 00074B616E7A6C6569
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300
          Cell 03 - Address: C4:3D:C7:50:7F:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/100  Signal level=48/100  
                    Encryption key:on
                    ESSID:"EDLIRA-PC_Network_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000020edfc9185
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 001345444C4952412D50435F4E6574776F726B5F31
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010F66226E1F777708BC99D1E6CBF876DFF1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 04 - Address: 50:7E:5D:3C:DF:B0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/100  Signal level=12/100  
                    Encryption key:on
                    ESSID:"DimmuBorgirLAN666"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ac0804f160
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 001144696D6D75426F726769724C414E363636
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000B7A12
                    IE: Unknown: DD8E0050F204104A00011010440001021041000100103B0001031047001000000000000000030000507E5D3CDFB01021000B436F72706F726174696F6E102300094152563735324450571024000933302E30352E3231391042000B52323336313537323634321054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: 0706444520010D10
          Cell 05 - Address: FC:75:16:7B:28:4D
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=62/100  Signal level=62/100  
                    Encryption key:on
                    ESSID:"Westeros"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006eec728ad
                    Extra: Last beacon: 380ms ago
                    IE: Unknown: 00085765737465726F73
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020007127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD8D0050F204104A0001101044000101103B000103104700102880288028801880A880FC75167B284D10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400094449522D36313548311042000A314331303037343839201054000800060050F204000110110015442D4C696E6B2053797374656D204449522D363135100800020084103C000101


eth0      Interface doesn't support scanning.




```

---

### Post by YJLWPBD on 2013-08-31
I remember that one of the few times the laptop connected with the wifi the router was set to channel 1, instead of channel 8 which is the usual. I haven't tried changing the channel and I'll wait for your advice first.

---

### Post by praseodym on 2013-08-31
Obviously, its an usb-device?! Check:
```

lsusb
lsmod
```

---

### Post by YJLWPBD on 2013-08-31
Allright I saw what you meant there. I actually somehow resolved my problem yesterday (the irony...two days after posting this thread) by reinstalling the driver again. Thank you very very much for your help and I will mark this thread as solved :)

---

