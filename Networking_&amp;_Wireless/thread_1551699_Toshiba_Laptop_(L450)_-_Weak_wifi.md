---
title: "Toshiba Laptop (L450) - Weak wifi?"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by micha8l on 2010-08-12
Hello

I've got a [Toshiba Satellite L450]("http://laptops.toshiba.com/laptops/satellite/L450")  laptop that has the latest stable version of Ubuntu. The wi-fi  connection on the laptop does work, and at times even reaches speeds of  800kb/s. But the connection is very volatile :p it seem to turn itself  on/off at its will. I've tried timing the connection losses but they're  random. In network connections my wi-fi connection has no BSSID or MAC  specified yet it still connects, but could this be the issue. Oh, and  I'm picking up neighbour's wi-fi connections too, could they maybe be  interfering with mine?

Any help would be appreciated!

Kind Regard
Mike

---

### Post by bkratz on 2010-08-12
> **micha8l said:**
> Hello

I've got a [Toshiba Satellite L450]("http://laptops.toshiba.com/laptops/satellite/L450")  laptop that has the latest stable version of Ubuntu. The wi-fi  connection on the laptop does work, and at times even reaches speeds of  800kb/s. But the connection is very volatile :p it seem to turn itself  on/off at its will. I've tried timing the connection losses but they're  random. In network connections my wi-fi connection has no BSSID or MAC  specified yet it still connects, but could this be the issue. Oh, and  I'm picking up neighbour's wi-fi connections too, could they maybe be  interfering with mine?

Any help would be appreciated!

Kind Regard
Mike

The BSSID and MAC don't need filled in: I have none either.  You might go to the terminal (Applications>>Accessories>>Terminal) and enter in 

```
sudo iwlist scan

```

It will require your password which will not be echoed-just hit enter when done.  Copy/paste the output back here so we can see your signal strength and possible sources of channel conflict.

---

### Post by micha8l on 2010-08-12
Hello thanks for the reply, I ran your command and it gave me the following:

```
          Cell 08 - Address: 00:24:17:ED:47:E1
                    ESSID:"michael"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-65 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 153ms ago

```

Kind Regards
Mike

---

### Post by bkratz on 2010-08-12
> **micha8l said:**
> Hello thanks for the reply, I ran your command and it gave me the following:

```
          Cell 08 - Address: 00:24:17:ED:47:E1
                    ESSID:"michael"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-65 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 153ms ago

```

Kind Regards
Mike

The signal strength looks good, the bit rate says 130Mbps (n)--did you remove any other "Cells" listed that show up as channel 1?

---

### Post by micha8l on 2010-08-12
No, I'm the only one on channel 1. My laptop's approximately 7.3M away  from the router and there's 2 dry walls in the way, the laptop's on  floor 2 and the router on floor 1. The router is  [BT Home Hub v2.0]("http://www.frequencycast.co.uk/homehub2.html").

Kind Regards

---

