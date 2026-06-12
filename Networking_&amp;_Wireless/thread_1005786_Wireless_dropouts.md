---
title: "Wireless dropouts"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by muguwmp67 on 2008-12-08
My laptop is disconnecting from my wireless network every 10-15 minutes.  The router is a WNDR3300 and my wireless card is a Trendnet TEW-501PC (Atheros AR5006XS chipset).

Things I've tried so far:
-  Changed mode of router from "up to 270Mbps at 2.4 GHz" to "up to 130Mbps at 2.4 GHz"
-  Used  "iwlist ath1 scan" to see what channels other networks in my neighborhood were using.  All were using channel 6, so I changed the router channel to 11.
-  Moved router farther away from the computer

It still disconnects all the time.  Interestingly my Xbox 360 is also wireless, is in the same room as my laptop and rarely disconnects.

Current iwlist for my network:
```
          Cell 02 - Address: 00:1F:33:B4:F4:9B
                    ESSID:"mugwump67"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

```

---

