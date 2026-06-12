---
title: "intel PRo / wireless 2915 AGB and wpa."
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by qrlgftrt on 2006-07-13
hello,

I have a fresh install of Dapper and want to connect to the internet via WI-FI with WPA-PSK security. Networks settings indicates the wireless interface eth1 is active, i can see the networks in my area. I select my network and fill in the WEP key (no other options there). Then I choose eth1 as default gateway device, In connection properties, I also choose eth1 as conneciton. After this, it shows me the connection strength is 0% and the wireless connection is disconnected. What is missing?

I was looking for a guide for installing/fixing WPA in Dapper but only found out that it is supposed to just work, so now I am clueless. What's wrong?

thx

---

### Post by qrlgftrt on 2006-07-13
more info:

```
chris@dell-cf:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"My-lan"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chris@dell-cf:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
chris@dell-cf:~$ iwlist my-lan scanning
my-lan    Interface doesn't support scanning.

chris@dell-cf:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:01:E3:59:57:39
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=70/100  Signal level=-58 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 1896ms ago
          Cell 02 - Address: 00:03:2F:1D:57:7D
                    ESSID:"My-lan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=91/100  Signal level=-38 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1780ms ago
          Cell 03 - Address: 00:01:E3:C4:5F:33
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=41/100  Signal level=-76 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 6708ms ago
          Cell 04 - Address: 00:13:D4:6E:FA:6C
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=35/100  Signal level=-79 dBm
                    Extra: Last beacon: 11212ms ago
          Cell 05 - Address: 00:50:8B:99:32:10
                    ESSID:"Likita"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=70/100  Signal level=-58 dBm
                    Extra: Last beacon: 4360ms ago
          Cell 06 - Address: 00:17:31:04:02:01
                    ESSID:"DGW"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=37/100  Signal level=-78 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1796ms ago
```

---

