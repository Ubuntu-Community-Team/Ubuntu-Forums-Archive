---
title: "Network manager essid problem"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by grantmeaname on 2011-05-14
I'm running maverick (no luck with natty), but a relatively new install. Ethernet works brilliantly. Last time I installed maverick the wireless worked out of the box, but I've had no such luck. I can't see any networks in the Network connections applet. I have the Intel 5300 wireless card. Yes, the drivers work. No, it's not being disabled by rfkill, I've checked. When I run 'iwlist wlan0 scan' I get nothing, but if I run it as root I get the following:
```
 Cell 01 - Address: 00:0B:86:E1:64:61
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"osuguest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f759e48eb
                    Extra: Last beacon: 5790ms ago
                    IE: Unknown: 00086F73756775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:0B:86:90:99:A1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"osuguest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000089c1892
                    Extra: Last beacon: 5790ms ago
                    IE: Unknown: 00086F73756775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:0B:86:92:00:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"osuguest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000371809d2a
                    Extra: Last beacon: 5710ms ago
                    IE: Unknown: 00086F73756775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:0B:86:E1:5E:20
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001bb75496
                    Extra: Last beacon: 5710ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800002A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:0B:86:E1:5E:21
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"osuguest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001bb75749
                    Extra: Last beacon: 5710ms ago
                    IE: Unknown: 00086F73756775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 56:E7:D1:BF:EA:4F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000167c618d94b47
                    Extra: Last beacon: 5700ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
          Cell 07 - Address: 00:0B:86:E1:31:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000fcaf48b82d
                    Extra: Last beacon: 5600ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800002A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:0B:86:E1:6A:41
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"osuguest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001de8345d74
                    Extra: Last beacon: 5590ms ago
                    IE: Unknown: 00086F73756775657374
                    IE: Unknown: 01088B0C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:0B:86:E1:67:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a60720181
                    Extra: Last beacon: 5590ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088B160C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800002A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: 00:0B:86:E1:64:70
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b273ba037
                    Extra: Last beacon: 2510ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 11 - Address: 00:0B:86:E1:6A:50
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000111412037
                    Extra: Last beacon: 5150ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 050402030000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 12 - Address: 00:0B:86:E1:5E:30
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b23a9037
                    Extra: Last beacon: 5030ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: Unknown: 050401030000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 13 - Address: 00:0B:86:92:00:A8
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"osuwireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000317dd6238d
                    Extra: Last beacon: 3280ms ago
                    IE: Unknown: 000B6F7375776972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000

```
That is, it can see osuwireless, the network I want to connect to, fine. Manually configuring the osuwireless network in Network Connections does nothing. the ESSID was set to OFF/ANY, but I changed it to 'osuwireless'; this also didn't help.

What do I do?

---

### Post by grantmeaname on 2011-05-18
So it looks like a reinstall is my only option?

---

