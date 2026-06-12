---
title: "Intermitent Wireless RTL8188CE ASUS PCIE N-15"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Troy^ on 2012-04-28
I just recently put together a computer with a ASUS PCIE N-15 802.11N wireless card. The card seems to be very intermitent, slow etc. random no internet access. the interment is also evident when ftp transferring. The transfer rate is periodically speeds up and slow down on my LAN. This card is everything but trouble even when surfing the internet as it will timeout connections to webpage because of the indeterminacy.  Although this card works flawlessly in Windows 7 it is not a hardware issue. Seems to be a driver or some sort of configuration issue.


Here is my lspci -v
> 01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 84b6
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at e000 [size=256]
        Memory at fea00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl8192ce
        Kernel modules: rtl8192ceHere is my modinfo:
> 
[LIST=1]
[*]troy@HTPC:~$ modinfo rtl8192ce
[*]filename:       /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
[*]firmware:       rtlwifi/rtl8192cfwU_B.bin
[*]firmware:       rtlwifi/rtl8192cfwU.bin
[*]firmware:       rtlwifi/rtl8192cfw.bin
[*]description:    Realtek 8192C/8188C 802.11n PCI wireless
[*]license:        GPL
[*]author:         Larry Finger    <[EMAIL="Larry.Finger@lwfinger.net"]Larry.Finger@lwfinger.net[/EMAIL]>
[*]author:         Realtek WlanFAE <[EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL]>
[*]author:         lizhaoming      <[EMAIL="chaoming_li@realsil.com.cn"]chaoming_li@realsil.com.cn[/EMAIL]>
[*]srcversion:     216E9AAB4459E49C3C6B69A
[*]alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
[*]alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
[*]alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
[*]alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
[*]depends:        rtlwifi,rtl8192c-common,mac80211
[*]intree:         Y
[*]vermagic:       3.2.0-24-generic SMP mod_unload modversions
[*]parm:           swenc:Set to 1 for software crypto (default 0)
[*] (bool)
[*]parm:           ips:Set to 0 to not use link power save (default 1)
[*] (bool)
[*]parm:           swlps:Set to 1 to use SW control power save (default 0)
[*] (bool)
[*]parm:           fwlps:Set to 1 to use FW control power save (default 1)
[*] (bool)
[*]parm:           debug:Set debug level (0-5) (default 0) (int)
[/LIST]

Please any guidance or help would be appreciated.

---

### Post by chili555 on 2012-04-28
May I please see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```Thanks.

---

### Post by Troy^ on 2012-04-28
Here you go:
```

troy@HTPC:/etc/modprobe.d$ cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
minstrel_ht
troy@HTPC:/etc/modprobe.d$

```

---

### Post by chili555 on 2012-04-28
> minstrel_htPerfect. Let's dig deeper. Please try:```
sudo modprobe -r rtl8192ce 
sudo modprobe rtl8192ce swenc=1
```May we see:```
sudo iwlist wlan0 scan
```

---

### Post by Troy^ on 2012-04-28
> **chili555 said:**
> Perfect. Let's dig deeper. Please try:```
sudo modprobe -r rtl8192ce 
sudo modprobe rtl8192ce swenc=1
```May we see:```
sudo iwlist wlan0 scan
```


So here we go:
```
sudo modprobe -r rtl8192ce ->returned nothing and my wireless 
disconnected and could not be reconnected.

sudo modprobe rtl8192ce swenc=1 ->reconnected





```
```
wlan0     Scan completed :
          Cell 01 - Address: 00:26:88:EB:14:B0
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Irvine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a3bd1b5195
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 0006497276696E65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16040D1600000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B0001031047001085C04BECA5FA3915BE4141F0BC9EAD5C1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180205F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D1600000000000000000000000000000000000000
          Cell 02 - Address: A8:39:44:5D:03:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"BELLALIANT600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000620c6521666
                    Extra: Last beacon: 1784ms ago
                    IE: Unknown: 000D42454C4C414C49414E54363030
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B00010310470010715FDFED29B2A357D7EFA7991961CE301021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 03 - Address: A8:39:44:52:5B:10
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"BELLALIANT620"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000393a161950c
                    Extra: Last beacon: 1908ms ago
                    IE: Unknown: 000D42454C4C414C49414E54363230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B000103104700101CAA2DA93FC6CB780201EEBDE6367D0A1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 04 - Address: 48:5B:39:F9:BB:C8
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013dedd8170
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604050600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010079127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404050600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 05 - Address: 00:1C:10:26:30:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023a21a3c59
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000
          Cell 06 - Address: 00:22:6B:51:89:75
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Hill"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004a1b374d4e
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 000448696C6C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD710050F204104A0001101044000102103B0001031047001000226B51897300226B5189730400E8001021000C4C696E6B73797320496E632E102300075752543331304E1024000776312E30302E34104200033030301054000800060050F2040001101100075752543331304E100800020088
                    IE: Unknown: DD090010180201F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 07 - Address: 00:1B:11:EC:9C:2A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"funnycow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f4647e019
                    Extra: Last beacon: 572ms ago
                    IE: Unknown: 000866756E6E79636F77
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340900050000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160900010000000F000000000000000000000000000000
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700103B76A598EE413E249574FAD25875F6531021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110019576972656C6573732044726166742031316E20526F75746572100800020004
          Cell 08 - Address: 00:18:E7:E4:A1:9A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"bernie2pots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a8ead3230
                    Extra: Last beacon: 596ms ago
                    IE: Unknown: 000B6265726E696532706F7473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B00000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409070300000000000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 09 - Address: A8:39:44:54:F0:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"BELLALIANT660"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000099ba61e3b5
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 000D42454C4C414C49414E54363630
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 10 - Address: 58:6D:8F:B4:85:27
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"D & E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000620cbcde183
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00054420262045
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B000103104700108FEAE67C490B78C4C1012063F04461A710210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```

---

### Post by chili555 on 2012-04-28
So with the change of swenc=1, are your connections more stable?> Cell 01 - Address: 00:26:88:EB:14:B0
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Irvine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a3bd1b5195
                    Extra: Last beacon: 228ms ago
                    I<snip>
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    <snip>
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    <snip>You may have better luck with WPA2 only instaed of mixed mode WPA and WPA2. You might also try different channels especially 1 or 11.

---

### Post by Troy^ on 2012-04-28
It seems to be abit better. There is alot of wireless access points in my neighborhood so channel 11 may not be the best choice? I switched to WPA2 to see if that works. Overall seems abit more stable which is weird but data transfer fluctuate quite weird.

---

### Post by Troy^ on 2012-04-28
Actually same issues as before. :( I wish I didn't get this card. I thought things were looking better but things are the sameway.

---

### Post by chili555 on 2012-04-28
I wonder if power management is in place:```
iwconfig
```

---

### Post by Troy^ on 2012-04-28
That is exactly what I was thinking power management. Due to the params in the modinfo output. Although I have no idea how it works or how to change it but here is the output iwconfig:
```

troy@HTPC:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Irvine"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:26:88:EB:14:B0
          Bit Rate=300 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

eth0      no wireless extensions.

```

I'm also getting like 3-5mbit transfer download and upload.

---

### Post by chili555 on 2012-04-28
> Power Management:[COLOR="Red"]off[/COLOR]Nothing to fix here. I'm sorry, I'm out of ideas/mojo/talent.

---

### Post by Troy^ on 2012-04-28
Thank you for the help chilli555 you were patient and helped out the best you could but if you could suggest a good PCI-E wirless card that does 300mbps that is fully supported and operational inside ubuntu/linux.. Unless there is someone else out there with any more ideas and thoughts.

---

### Post by Troy^ on 2012-04-28
Anyone else have any help/ideas?

---

### Post by Troy^ on 2012-04-29
bump?

---

### Post by uylug on 2012-04-29
Once you're connected, try:

```
sudo iwconfig wlan0 retry 255
```

Not a permanent fix but it might help you detect possible issues.

A higher number may also work, something like 99999.

---

### Post by maciej234 on 2012-04-29
you could try installing the realtek linux driver. there are two rtl8192ce's drivers for linux

---

### Post by Troy^ on 2012-04-30
That is what i was thinking of trying but I have no idea how to use the downloaded drivers i have.

---

### Post by uylug on 2012-04-30
> **Troy^ said:**
> That is what i was thinking of trying but I have no idea how to use the downloaded drivers i have.

Didnt my command work?

I remember having a lot of issues with my RTL8187B, since Ubuntu 8.04 and using ndiswrapper for it to work, but it worked fine.

I remember using the command I wrote to fix issues with the **open source** driver though, the proprietary seemed to work just fine.

You could try my command and see if it works and if not, try using ndiswrapper.

---

### Post by maciej234 on 2012-04-30
> **Troy^ said:**
> That is what i was thinking of trying but I have no idea how to use the downloaded drivers i have.

Download the LINUX driver here: ( i downloaded the RTL8192CE-VA4 version)

1.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true)

Follow these steps to install:

2.
[http://www.youtube.com/watch?v=QFh2EZhUKgs](http://www.youtube.com/watch?v=QFh2EZhUKgs)

3. open in terminal: gksu gedit /etc/modprobe.d/blacklist.conf

add this phrase:  blacklist rtl8188ce

4.  open in terminal:   gksudo gedit /etc/modules

add this phrase:  rtl8192ce

5.  delete the current wireless network, restart computer, and connect to wireless, add password

---

### Post by Troy^ on 2012-04-30
Alright Thanks. I'll give this a try when I get home. There is nothing to loose anyways as i had to resort dual booting windows to have proper use of this wireless card.

---

### Post by maciej234 on 2012-04-30
> **Troy^ said:**
> Alright Thanks. I'll give this a try when I get home. There is nothing to loose anyways as i had to resort dual booting windows to have proper use of this wireless card.


Just to add- you might have to turn off the wireless via the bios and reboot and enable it again.  check speakeasy speed test.com to see your download speeds.  I had to use the fn+wireless off/on on my thinkpad after i setup the network. so far speeds have been fine

---

### Post by Troy^ on 2012-05-01
I tried installing the new drivers and everything seemed fine and i rebooted and it made the consisteincy even worse. My Download and Upload were 1mbit/1mbit and I'm on a 30mbit/30mbit connection and get those numbers in Windows 7 with the same card. I used the RTL8192CE-VA4 drivers. Perhaps this is the wrong one?

---

### Post by maciej234 on 2012-05-02
My connections speeds also varied.

I did fresh install and turned off the power management on the wireless. Connection appears better

you could try in terminal:

sudo iwconfig wlan0 power off

to make permanent:

[http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641)

gksu gedit /etc/pm/power.d/wireless and then I just put 
     Quote:
                                                 #!/bin/sh

/sbin/iwconfig wlan0 power off                                 
In the file.

Lastly, 
     Code:
     sudo chmod +x /etc/pm/power.d/wireless

---

