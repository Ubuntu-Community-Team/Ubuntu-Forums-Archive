---
title: "not connecting to wireless router comtrend CT-536T"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by mibungu on 2011-01-29
Hi another company came with their router comtrend CT-536T but now my laptop lenovo r61i is not able to connect to it. like it has a issue with wap/wap1. Is their a possibility to get it to connect. the other router maxG (US robotics) is wep/hex based. any suggestions ? It only made a connection the first time and after the signal wasn't even noticeable :(. now I see it but can't make a connection.

---

### Post by mibungu on 2011-01-31
Scan completed :
          Cell 01 - Address: 00:14:C1:46:87:2B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"WiFi_Frangie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000027ed44c24
                    Extra: Last beacon: 13284ms ago
                    IE: Unknown: 000C576946695F4672616E676965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DDB50050F204104A00011010440001021041000100103B000103104700100014C146872A0014C146872A00C490A010210019552E532E20526F626F7469637320436F72706F726174696F6E1023001F5553526F626F7469637320576972656C657373204D41586720526F7574657210240007555352353436351042000533343630321054000800060050F20400011011001F5553526F626F7469637320576972656C657373204D41586720526F75746572100800020088
                    IE: Unknown: DD090010180202F4000000
          Cell 02 - Address: 00:1A:2B:4E:75:D7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"TeleW-KMNWKN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027c28a4183
                    Extra: Last beacon: 11508ms ago
                    IE: Unknown: 000C54656C65572D4B4D4E574B4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


as you see I attempted to connect and run a iwlist scan, I post here both connection router that works and the second one which connects for a minute or so and stops.

---

### Post by mibungu on 2011-02-01
well only when another laptop connects I seem to be able to connect. I see I connect on channel 11, probably the windows box on channel 1. I don't know whether ndiswrapper will fix it without this strange other laptop having to "pre-connect".

---

