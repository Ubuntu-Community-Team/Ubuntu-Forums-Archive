---
title: "broadcom STA: Is 802.11n the default?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Camaguey on 2010-02-17
How can I make sure that of the g and n frequencies that my router is broadcasting, wicd is connecting to the n? My bcm4322 chip supports n, and can connect to an n-only network. 

A speed test may prove one over th other, depending on the overall speed, but is there a more exact way of knowing?

---

### Post by northd_tech on 2010-02-18
It will probably depend upon what kind of WiFi access points you have available.  I have found the 802.11n to be extremely rare in my travels.  I use my Broadcom 4321AG to connect to a 5.77 GHz N-speed Apple AirPort at work around 230 Mbps usually, but our "bottlenecked" ISP crawls along in the DSL-T1 range (about 1-3 Mbps), so why would N matter if I could ever theoretically even reach it?  I'd love to get back to those good ol' 54 Mbps 802.11g speeds if I had the chance (that would be a **big** improvement over what I've seen lately).

BTW- that is the "improved" DSL-ish speed after I just fixed the "IPv6" slow connection problem earlier today (with some kernel options in my GRUB menu.lst configuration).

My Broadcom 4321AG is reported by **lspci** as a 4328, but it shares much with your 4322 I believe (including the STA driver and 802.11n).

If you are curious, enter this code from a terminal and maybe post the results here:

```
sudo iwlist scan
```

---

### Post by Camaguey on 2010-02-27
O.O I didn't know you could do that. I'm connected to Cell 01. Does this also give any hints on improving speed?
```

eth1      Scan completed :
          Cell 01 - Address: 00:22:B0:B5:51:75
                    ESSID:"thegame"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010459D09F98DA5332A9494FC65F0FC41E81021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020084
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

---

