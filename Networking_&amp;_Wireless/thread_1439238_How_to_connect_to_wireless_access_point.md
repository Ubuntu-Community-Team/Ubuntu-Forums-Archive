---
title: "How to connect to wireless access point"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by rapc0d on 2010-03-25
hello friend i've finish install driver for my wireless adapter and the result like this:
```

rapc0d@rapc0d-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rapc0d@rapc0d-laptop:~$

```

and then i've scan the access point and the result like this :
```

rapc0d@rapc0d-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:1F:1E:5F:B4
                    ESSID:"Super2"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=69/100  Signal level=-68 dBm  Noise level=-104 dBm
                    Extra: Last beacon: 34ms ago
          Cell 02 - Address: 00:0E:2E:E1:B4:52
                    ESSID:"Super1"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-68 dBm  Noise level=-102 dBm
                    Extra: Last beacon: 33ms ago
          Cell 03 - Address: 00:25:4E:00:61:E0
                    ESSID:"GORANGO"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-68 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 211ms ago

rapc0d@rapc0d-laptop:~$

```

and the question how i can connect to that ?
thanks

rapc0d,

---

### Post by chili555 on 2010-03-26
Please see:  [http://ubuntuforums.org/showpost.php?p=9029695&postcount=4](http://ubuntuforums.org/showpost.php?p=9029695&postcount=4)

---

