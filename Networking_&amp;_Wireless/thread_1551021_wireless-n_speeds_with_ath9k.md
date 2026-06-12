---
title: "wireless-n speeds with ath9k?"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by evanct on 2010-08-11
I have a new D-link DWA-556(AR5008 ) wireless adapter that I got working using the ath9k driver, and a Linksys WRT100N router. I can't seem to enable 802.11n speeds. The default bitrate is 1 Mb/s, and when I use
```
iwconfig wlan0 rate [value]
```
The highest rate I can set is 54M - anything higher than that and it complains that I'm using an invalid argument. Here's the full output of iwconfig:

```
wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:59:04:0E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I thought ath9k was supposed to support 802.11n?

I'm using 10.04 64-bit, if it matters.

---

### Post by evanct on 2010-08-11
oh and iwlist wlan0 scan shows that the max rate is 54:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:59:04:0E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002427278e36
                    Extra: Last beacon: 66690ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F0500000000000000000000000000000000000000
```

---

