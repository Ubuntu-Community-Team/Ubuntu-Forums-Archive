---
title: "wicd"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-01-07
Wicd is saying "Bad Password" upon a connection to my network.....

i have 

```
sudo apt-get remove network-manager
```

```
toews@desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:4A:DF:5A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"toews"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000032fcd5181
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 0005746F657773
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F010100060000
                    IE: Unknown: DD0C00037F020101020002A34000
                    IE: Unknown: DD0600032F010001

```

---

