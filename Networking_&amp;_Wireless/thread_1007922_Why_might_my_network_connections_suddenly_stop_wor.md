---
title: "Why might my network connections suddenly stop working?"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by SlaughterDog on 2008-12-10
I've got an Acer Aspire One and got the wireless working with ath5k drivers. However, suddenly, it quit working. The thing is, it worked for a while, but today I was using it and suddenly it lost the wireless connection and would not connect again. I figured perhaps something had blocked the signal. I went home to find it won't connect to my wireless network either, and the network manager icon won't show any wireless networks either.

So, I hooked up to my ethernet for a temporary connection, then suddenly that quits working too!

Any ideas?

---

### Post by superprash2003 on 2008-12-11
post output of iwlist scan from the terminal

---

### Post by SlaughterDog on 2008-12-12
Suddenly, it works again. I need this to be more reliable though.
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:1C:73:57
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/100  Signal level:-63 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000013f6e335189
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: 00:12:17:1C:73:57
                    ESSID:"Todd's House"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=75/100  Signal level:-48 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: Unknown: 000C546F6464277320486F757365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000013f6e0717f8
                    Extra: Last beacon: 2920ms ago

pan0      Interface doesn't support scanning.

```

---

### Post by superprash2003 on 2008-12-13
well its available to scan for wifi networks.. have you tried connectin manually to a network ? using network manager?? i mean this way .. if you are on ubuntu 8.10 you need to install old network manager ( its better ) [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) follow till step 4 . then connect manually like this [http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html](http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html)

---

