---
title: "How to differentiate the encryption type used for wireless network"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by predatorz on 2010-02-09
Hi,

Using sudo iwlist scan, i will get a list of surrounding AP(s) around my laptop, is there a way to interpret the sudo iwlist scan results so that we can know what encryption type is the wireless network using?

---

### Post by chili555 on 2010-02-09
Here is a scan result with no encryption:> Cell 02 - Address: 88:1C:DF:52:88:88
                    ESSID:"lazy1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="Blue"]Encryption key:off[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    Extra: Last beacon: 9432ms agoAnd here is WEP:>  Cell 01 - Address: 99:12:99:46:99:76
                    ESSID:"WEPisalrite"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR="Blue"]Encryption key:on[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 9556ms agoAnd, finally, here is WPA:> Cell 01 - Address: 77:78:79:etc.
ESSID:"mynetwork"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:43/100 Signal level:-68 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: [COLOR="Blue"]IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK 

---

### Post by predatorz on 2010-02-10
Seeing your output for WPA network, how to tell if it is on WPA2/WPA?
Is it correct to say it is on WPA2 since WPA2 output is before WPA?

Cell 01 - Address: 77:78:79:etc.
ESSID:"mynetwork"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:43/100 Signal level:-68 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: [COLOR=Blue]IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK

---

### Post by sgosnell on 2010-02-10
Here's a WPA cell: ```


          Cell 03 - Address: 00:1F:B3:B9:85:F1
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE961"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ea38e752aa
                    Extra: Last beacon: 3836ms ago
                    IE: Unknown: 00083257495245393631
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    **IE: WPA Version 1**
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C 
```

WPA and WPA2 should be easy to distinguish.

---

