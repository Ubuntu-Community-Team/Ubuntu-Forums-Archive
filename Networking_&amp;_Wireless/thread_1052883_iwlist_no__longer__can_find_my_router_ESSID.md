---
title: "iwlist no _longer_ can find my router ESSID"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Reiger on 2009-01-28
Replaced my wireless router, set it up to match the old one and for some reason
```

iwlist wlan1 scan
```

can no longer find my Routers public ESSID. During setup there was a "default" ESSID assigned to my router which every now and then still 'haunts' the output, but my new (read: old) ESSID never appears in the output list. The other PC can still find and connect to the old/new ESSID without problems, so I guess the problem is with this one.

And yes, the ESSID I expect to find is public, and I am sitting next to the router so it can't be lack of signal strenght either. ;)

```
sudo iwlist wlan1 scanning
wlan1     Scan completed :                     
          Cell 01 - Address: 00:02:CF:73:B2:2B 
                    ESSID:"Bolpoint 7"         
                    Mode:Master                
                    Channel:7                  
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on                                         
                    IE: Unknown: 000A426F6C706F696E742037                     
                    IE: Unknown: 010582848B962C                               
                    IE: Unknown: 030107                                       
                    IE: Unknown: 2A0104                                       
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000d8fd71d1b6
                    Extra: Last beacon: 608ms ago
          Cell 02 - Address: 00:1E:E5:25:C9:0E
                    ESSID:"Bolpoint 7"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000A426F6C706F696E742037
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000002cbda6b4
                    Extra: Last beacon: 636ms ago
          Cell 03 - Address: 00:11:6B:13:10:EA
                    ESSID:"default"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:off
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010A
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001a3b2b2cc54
                    Extra: Last beacon: 556ms ago


```

Would anyone happen to know if there is some way to 'reset' the iwlist tool?

---

### Post by Reiger on 2009-01-28
Solved the problem by changing ESSID in the router... Odd, though because I checked and Windows Vista *could* find that old ESSID just fine.

Are there any iwlist configuration/log (or other storage) files I might've messed up?

---

