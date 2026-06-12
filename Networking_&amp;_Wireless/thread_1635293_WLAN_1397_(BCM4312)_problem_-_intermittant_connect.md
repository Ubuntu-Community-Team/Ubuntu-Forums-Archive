---
title: "WLAN 1397 (BCM4312) problem - intermittant connectivity"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by rpalmer on 2010-12-01
Let me preface this question by saying that I've searched google and the Ubuntu forums and I haven't found a solution that matches the problem I'm having. 

As stated I'm using a Dell WLAN 1397 half-mini card (BCM4312) and running Ubuntu 10.10.  I can connect to my Wireless AP but I am having problems maintaining a good connection. For example when I go to download a file it will download 300 bytes and completely choke...

I had the same problem with Windows 7 but I fixed it by going into advanced options on the device manager and changing a setting from "Best Performance" to "Broad Compatibility" but I am not sure how I would change this in Ubuntu.  Is there a file that can be edited with those options?  How should I proceed?

Thanks in advance for any help!

---

### Post by uncaspi on 2010-12-01
Please post the content of sudo iwlist scan
and tell us what's your router.

The only command I could think of matching windows is open a terminal
and issue sudo iwconfig wlan0 sens -80

Replace wlan0 with your interface if it's not wlan0

---

### Post by rpalmer on 2010-12-01
I have a WAP54G (access point only) that connects to a firewall ( no wireless).

Results of "sudo iwlist scan"

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:74:E6:AA
                    ESSID:"WIFI"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:21:29:7F:B5:BD
                    ESSID:"jason"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:1D:5A:CC:BC:11
                    ESSID:"2WIRE557"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303436303731313131303535371021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3436303731313131303535371054000800060050F20400011011000A686F6D65706F7274616C10080002008E
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:0F:B5:EA:5C:1A
                    ESSID:"603544"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:25:3C:77:A5:19
                    ESSID:"2WIRE605"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303233303931393032313630351021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3233303931393032313630351054000800060050F20400011011000A686F6D65706F7274616C10080002008E
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by rpalmer on 2010-12-08
The problem was caused by my firewall.  I reset it to factory defaults and it fixed the problem.

---

