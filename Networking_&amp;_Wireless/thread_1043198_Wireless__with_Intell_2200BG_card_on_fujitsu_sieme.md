---
title: "Wireless  with Intell 2200BG card on fujitsu siemens laptop"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by theopDK on 2009-01-18
Hello. I recently bought me a used Fujitsu Siemens Amilo M1425 laptop, and installed ubuntu 8.10 on it. It all runs fine except for my wireless network. I simply can not make it work. Network Manager (both tried Knetwork manager and preinstall) finds my wireless connection, but will not sign on it. I enter all the right information on the for the login, but it still does not bother to connect to. Missing a driver I might? Or what do I do wrong? 

Thank you in advance 

Sincerely, the happy, albeit slightly frustrede new Ubuntu user

oh, ps: my network card is: Intel Corporation PRO/Wireless 2200BG

---

### Post by superprash2003 on 2009-01-18
post output of **iwlist scanning**

---

### Post by theopDK on 2009-01-27
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:35:0D:D0
                    ESSID:"elevnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Extra: Last beacon: 2956ms ago
          Cell 02 - Address: 00:1B:2F:35:0D:98
                    ESSID:"elevnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-38 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Extra: Last beacon: 96ms ago
          Cell 03 - Address: 00:1B:2F:35:0C:E0
                    ESSID:"elevnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Extra: Last beacon: 808ms ago
          Cell 04 - Address: 00:13:F7:81:11:69
                    ESSID:"JRR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-81 dBm  
                    Extra: Last beacon: 2832ms ago
          Cell 05 - Address: 00:1B:2F:CE:18:38
                    ESSID:"elevnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=53/100  Signal level=-69 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    Extra: Last beacon: 208ms ago

pan0      Interface doesn't support scanning.

---

### Post by peachtree195 on 2009-09-14
Hello more experienced ones!

I have a similar problem with my fujitsu amilo pro v8010, wireless intell 2200BG card - the system sees the wireless card, it says the card is active, but it just does not see the wireless networks around me.

here is some data from [B]iwlist scanning:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:A6:E8:0A
                    ESSID:""
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=68/100  Signal level:-44 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: Unknown: 0003000000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000cc12797540
                    Extra: Last beacon: 44ms ago

pan0      Interface doesn't support scanning.
[/B]
I hope someone helps here!
Thanks a lot!

---

