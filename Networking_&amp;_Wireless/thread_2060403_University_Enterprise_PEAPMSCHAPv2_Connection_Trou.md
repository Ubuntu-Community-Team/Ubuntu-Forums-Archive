---
title: "University Enterprise PEAP/MSCHAPv2 Connection Troubles"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by peejaroni on 2012-09-20
Hi all, 
The title pretty much says it all, when trying to connect I've entered my password, PEAP version 0, mschapv2, and everything looks right. Network Manager keeps trying to connect, until it stalls out and asks for my password again. 

Any help would be greatly appreciated!

---

### Post by ajmorris on 2012-09-21
> **peejaroni said:**
> Hi all, 
The title pretty much says it all, when trying to connect I've entered my password, PEAP version 0, mschapv2, and everything looks right. Network Manager keeps trying to connect, until it stalls out and asks for my password again. 

Any help would be greatly appreciated!

Hi there,
What application are you using to try and connect to the network? Can you post that along with the current configuration in there, and any settings of the target AP you're trying to connect to, both your own information provided by the university, as well as the output of ```
sudo iwlist scanning
``` (assuming you have wireless-tools installed)

As a side note you might want to try before posting the information, many enterprises including universities require a domain suffix on your user id, i.e. [email]user@domain.exampl[/email]e is the syntax of your user id.

AJ

---

### Post by peejaroni on 2012-09-21
Thanks for helping! 
I'm currently using NetworkManager/nm-applet to connect, although I've tried using wicd before to the same result. 

My current security settings are the same ones the university tells us to use for Android phones (and work for my Android phone): 
```

Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP) 
Anonymous identity: (blank) 
CA certificate: (none)
PEAP version: Version 0
Inner authentication: MSCHAPv2
Username: (my username)
Password: (my password)

```

I didn't find any details on the IT page about the network (although I have a few friends in IT I can ask if we find any specific questions)

The outpus was: 

```

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:1E:84:E2:E1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045ea04be64
                    Extra: Last beacon: 2832ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:1A:1E:8A:51:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cc368f50c
                    Extra: Last beacon: 2792ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:1A:1E:84:D7:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c6991d059
                    Extra: Last beacon: 2712ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:1A:1E:84:D3:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e6b6ee6e
                    Extra: Last beacon: 2380ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:1A:1E:84:D0:80
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e62ef180
                    Extra: Last beacon: 2348ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:1A:1E:8A:95:61
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001769b51a44
                    Extra: Last beacon: 2316ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:1A:1E:8A:4C:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d473a24b3
                    Extra: Last beacon: 2448ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:1A:1E:84:D3:A1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e6b55a44
                    Extra: Last beacon: 2484ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:1A:1E:8A:4C:21
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d473bbd6f
                    Extra: Last beacon: 2340ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: 00:1A:1E:84:E2:F0
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000df2c15884e
                    Extra: Last beacon: 2136ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16300708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34300708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 11 - Address: 00:1A:1E:8A:0E:D0
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012c49a2859
                    Extra: Last beacon: 400ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16950508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34950508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 12 - Address: 00:1A:1E:8A:0E:D1
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012c49a29ff
                    Extra: Last beacon: 400ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16950508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34950508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 13 - Address: 00:1A:1E:8A:4D:10
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d6287857
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16950508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34950508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 14 - Address: 00:1A:1E:8A:4D:11
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d62879fe
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16950508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34950508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 15 - Address: 00:1A:1E:8A:42:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cb16edc5d
                    Extra: Last beacon: 2844ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 16 - Address: 00:1A:1E:8A:95:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001769b51180
                    Extra: Last beacon: 2316ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 17 - Address: 00:1A:1E:8A:A1:A1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df440ed28
                    Extra: Last beacon: 2284ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 18 - Address: 00:1A:1E:84:E3:61
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000104e98ea44
                    Extra: Last beacon: 2264ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 19 - Address: 00:1A:1E:84:E3:70
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1b31a5b7
                    Extra: Last beacon: 2244ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424050A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 20 - Address: 00:1A:1E:84:E3:71
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1b31a75d
                    Extra: Last beacon: 2244ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424050A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 21 - Address: 00:1A:1E:84:D0:90
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000446f6f50d
                    Extra: Last beacon: 2220ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16280708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34280708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 22 - Address: 00:1A:1E:84:D0:91
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000446f6f6b3
                    Extra: Last beacon: 2220ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16280708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34280708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 23 - Address: 00:1A:1E:8A:51:90
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000045b8ed553
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030199
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16990708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34990708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 24 - Address: 00:1A:1E:8A:51:91
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000045b8ed6f9
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030199
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16990708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34990708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 25 - Address: 00:1A:1E:8A:A1:10
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000431bc9036
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03019D
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D169D050A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C349D050A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 26 - Address: 00:1A:1E:8A:A1:11
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000431bc91b0
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03019D
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D169D050A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C349D050A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 27 - Address: 00:1A:1E:8D:71:70
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000059dbf61591
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0301A1
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16A10708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34A10708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 28 - Address: 00:1A:1E:8D:71:71
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000059dbf61738
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0301A1
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16A10708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34A10708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 29 - Address: 00:1A:1E:8A:50:D0
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007ef4af036
                    Extra: Last beacon: 2136ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: Unknown: 050400010100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16300708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34300708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 30 - Address: 00:1A:1E:8A:50:D1
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007ef4af1b0
                    Extra: Last beacon: 2136ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: Unknown: 050400010000
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16300708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34300708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 31 - Address: 00:1A:1E:8A:51:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cc368ec48
                    Extra: Last beacon: 2796ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 32 - Address: 00:1A:1E:8A:4D:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000efbe49fe6
                    Extra: Last beacon: 2680ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 33 - Address: 00:1A:1E:8A:0E:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000048b55c6265
                    Extra: Last beacon: 2636ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 34 - Address: 00:1A:1E:8A:0E:C1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000048b55b24a8
                    Extra: Last beacon: 2716ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 35 - Address: 00:1A:1E:8D:71:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a524fe88
                    Extra: Last beacon: 2708ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 36 - Address: 00:1A:1E:8D:71:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a5268a44
                    Extra: Last beacon: 2608ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 37 - Address: 00:1A:1E:8A:A1:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000038a752ab3
                    Extra: Last beacon: 2648ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 38 - Address: 00:1A:1E:84:E1:E0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e2da73180
                    Extra: Last beacon: 2696ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 39 - Address: 00:1A:1E:84:E1:E1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e2da73a44
                    Extra: Last beacon: 2696ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 40 - Address: 00:1A:1E:8A:A1:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df440e465
                    Extra: Last beacon: 2284ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 41 - Address: 00:1A:1E:8A:4C:30
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000972c57e
                    Extra: Last beacon: 2180ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D162C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C342C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 42 - Address: 00:1A:1E:8A:4C:31
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000972c725
                    Extra: Last beacon: 2180ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D162C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C342C0508000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 43 - Address: 00:1A:1E:8A:50:C0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000048a0878180
                    Extra: Last beacon: 2768ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 44 - Address: 00:1A:1E:84:E2:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045ea05c50b
                    Extra: Last beacon: 2764ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 45 - Address: 00:1A:1E:8A:A2:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ac08adba
                    Extra: Last beacon: 2820ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 46 - Address: 00:1A:1E:8A:4D:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000efbe38180
                    Extra: Last beacon: 2752ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 47 - Address: 00:1A:1E:84:E3:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000104e98e180
                    Extra: Last beacon: 2268ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 48 - Address: 00:1A:1E:84:E2:F1
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000df2c1589f4
                    Extra: Last beacon: 2132ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16300708000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34300708000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 49 - Address: 00:1A:1E:8A:A1:C1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1018d1f7
                    Extra: Last beacon: 2820ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 50 - Address: 00:1A:1E:8A:44:61
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000577ddaa44
                    Extra: Last beacon: 2852ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 51 - Address: 00:1A:1E:8A:42:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cb16ed399
                    Extra: Last beacon: 2844ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 52 - Address: 00:1A:1E:8A:50:C1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000048a0869d00
                    Extra: Last beacon: 2828ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 53 - Address: 00:1A:1E:8A:A1:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000038a739a33
                    Extra: Last beacon: 2748ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 54 - Address: 00:1A:1E:84:D7:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c69926f43
                    Extra: Last beacon: 2672ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 55 - Address: 00:1A:1E:8A:4C:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MyUniversity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dbbf5f180
                    Extra: Last beacon: 2492ms ago
                    IE: Unknown: 000C4E6F7274687765737465726E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 56 - Address: 00:1A:1E:8A:A2:B1
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"Guest-MyUniversity"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000015dda79f36
                    Extra: Last beacon: 2136ms ago
                    IE: Unknown: 001247756573742D4E6F7274687765737465726E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030130
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1630070A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3430070A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000

```

I want to connect to the "MyUniversity" network as opposed to the guest one. 

Once again, thanks for helping!

---

### Post by ajmorris on 2012-09-21
interesting, i dont see an issue with the configuration options for that type of network, and networkmanager should be more than capable of connecting to it... Double check your user id with domain, and password, and if there are no certificates that the network needs to download to allow authorisation, its very strange indeed. I imagine you've already double checked your user id and password anyway... so the next step would be to try a manual network connection without a NetworkManager daemon active... im at an android box atm, so i cant provide you with an example without it sitting in front of me... but if you want to try to get it to work before i get to one in a few hours, basically try googling something along the lines of "wpa_supplicant how to PEAP with mschapv2" there is hopefully some resources there, then basically make sure the NetworkManager daemon is stopped while running wpa_supplicant as they will conflict, if you cant find anything, ill post a config file for it later today. :)

---

### Post by peejaroni on 2012-09-22
I created the wpa_supplicant file, and ran followed the tutorial here: [http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup](http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup)

but ended up with the error, "ioctl[SIOCSIWENCODEEXT]: Invalid argument" showing up twice. 

Any idea if the error is with the tutorial, or the user (me)? 
Thanks!

---

### Post by ajmorris on 2012-09-23
> **peejaroni said:**
> I created the wpa_supplicant file, and ran followed the tutorial here: [http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup](http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup)

but ended up with the error, "ioctl[SIOCSIWENCODEEXT]: Invalid argument" showing up twice. 

Any idea if the error is with the tutorial, or the user (me)? 
Thanks!

Firstly, my apologies for not posting a configuration file, unforeseen circumstances prevented me from getting to a computer.

The tutorial looks fine, that error you're getting is generally from incorrect syntax in your /etc/wpa_supplicant.conf file, perhaps you missed a closing quotation mark or forgot to close the network bracket, however, i would first try a more basic connection without the need of certificates etc, unless your network explicitly requires them, just to see if you can get some handshaking happening. Try the following:

/etc/wpa_supplicant.conf:
```

network={
ssid="MyUniversity"
key_mgmt=WPA-EAP
eap=PEAP
identity="user@domain"
password="password"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}
```

then proceed to stop the NetworkManager daemon: 
```
sudo stop network-manager
```

then bring down your interface:
```
sudo ifconfig IFACE down
``` Where IFACE is your wireless card interface (should be wlan0 given the output of your previous post)

then bring the interface back up with the wpa_supplicant command:
```
sudo wpa_supplicant -Dwext -iIFACE -c/etc/wpa_supplicant.conf &
``` This line assumes you are using a native linux driver, rather than ndiswrapper.

```
sudo dhcpcd IFACE &
```

If you get problems, please post all terminal output from the above commands as well as the full output of the following:
```

sudo lspci -v && sudo lsmod
```

AJ

---

### Post by peejaroni on 2012-09-24
Ok, I think we are close, but no success quite yet. 

I end up with 
```
 dhcpcd: command not found
```
when I try to run that line. 

Here's the total output from everything (The last section with the invalid arguments, device or resource busy, Failed to initiate AP Scan, and trying to associate with... continue repeating while time goes on).  

```
Me:~$ sudo stop network-manager
network-manager stop/waiting
Me:~$ sudo ifconfig wlan0 down
Me:~$ sudo wpa_supplicant -Dwext -i wlan0 -c /etc/wpa_supplicant.conf &
[1] 32185
Me:~$ ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
Trying to associate with 00:1a:1e:8a:0e:c0 (SSID='MyUniversity' freq=2462 MHz)
CTRL-EVENT-DISCONNECTED bssid=00:1a:1e:8a:0e:c0 reason=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument

```


And the results of the lspci / lsmod were: 
```
Me:~$ sudo lspci -v && sudo lsmod
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f2625000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
	Memory at f262b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 5080 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21ce
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f262a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ce
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2500000-f25fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ce
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f1d00000-f24fffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f0bfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ce
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f1400000-f1cfffff
	Prefetchable memory behind bridge: 00000000f0c00000-00000000f13fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ce
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21ce
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f2629000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 21ce
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at 50a8 [size=8]
	I/O ports at 50bc [size=4]
	I/O ports at 50a0 [size=8]
	I/O ports at 50b8 [size=4]
	I/O ports at 5060 [size=32]
	Memory at f2628000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: medium devsel, IRQ 11
	Memory at f2624000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number a0-88-b4-ff-ff-7c-0f-80
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

0d:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 05) (prog-if 01)
	Subsystem: Lenovo Device 2133
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f1401000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [800] Advanced Error Reporting
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f1400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

Module                  Size  Used by
psmouse                87603  0 
iptable_mangle         12734  0 
iptable_nat            13229  0 
nf_nat                 25891  1 iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_filter         12810  0 
ip_tables              27473  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               29846  4 iptable_mangle,iptable_nat,iptable_filter,ip_tables
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62128  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
thinkpad_acpi          81819  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               328352  0 
snd_timer              29990  2 snd_pcm,snd_seq
mac80211              506816  1 iwlwifi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  2 iwlwifi,mac80211
nvram                  14413  1 thinkpad_acpi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
tpm_tis                18804  0 
mac_hid                13253  0 
wmi                    19256  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  5 
drm_kms_helper         46978  1 i915
drm                   242038  6 i915,drm_kms_helper
lp                     17799  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
parport                46562  3 parport_pc,ppdev,lp
e1000e                156693  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```

Once again, thank you very much for your help!

---

### Post by ajmorris on 2012-09-24
Sorry, the dhcpcd command should have been run with your dhcp client... i think dhclient is the default in ubuntu, not dhcpcd. And its good that it finds the AP now and can associate with it, the disconnect however, is not easy to debug. The error could be any number of things from a slight misconfiguration in the config file according to what the network wants, to the network booting you off for an unknown reason or the network may need a certificate that your wpa_supplicant is not communicating with... Its unlikely its a certificate error, as your uni should have put that information in their connectivity page. Do you have any other network daemons active that might be conflicting with it? The most common reason for that error on the local side is NetworkManager interfering with wpa_supplicant, but since you stopped the service, this shouldnt be the case. If its not a local conflict, you really need the server side logs to see if you're actually communicating with the network or if its failing before the server can even see you. Contacting the IT support of your uni should allow you to see the connectivity logs on the server side (unless they're being difficult) so we can figure out where to go next, just make sure you get full logs from them for your MAC address, and if you have a windows/OSX partition on the same machine it will make it difficult :P

As a side note, your wireless card thinks it is using the intel wireless kernel drivers which have been compiled into the kernel as a module, i.e. you can rmmod/modprobe the iwlwifi module to deactivate/reactivate the card. Have you got other drivers that may be conflicting with this one? Ndiswrapper or other third party drivers will conflict with it and that can also be the cause of your wpa_supplicant disconnects. Try running ```
sudo rfkill list all
``` to look for conflicts.

Can you also post the output of ```
 sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n75
``` After the NetworkManager daemon has been stopped, hopefully we can see if there is anything else conflicting.

AJ

---

