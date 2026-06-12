---
title: "[SOLVED] Wireless scan sees all networks except my own"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by AkuTenshi on 2008-12-22
Whenever I run iwlist eth1 scan, it returns the ESSIDs of the routers across the road (BTHomeHub-244E and wireless), but doesn't not see the one two meters from the computer (Tiger's Lair):```

laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:F6:99:AC:E1
                    ESSID:"BTHomeHub-244E"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:14:BF:B8:84:C5
                    ESSID:"wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

```

Other computers in my house, and the same computer under XP, can see my network. My network chip is the Broadcom BCM4312 802.11b/g (rev 01), for which I am using the wl driver that is suggested by the Ubuntu 'Hardware Drivers' application. It worked in the past, and I cannot think of anything I have done recently that could have affected it. I cant think how it could be my router, which is still visible/functional to other PCs.
Does anyone have an idea what the problem could be?

---

### Post by pytheas22 on 2008-12-22
Do you know which channel your router is operating on?  Some drivers (don't know about wl) may not be able to see routers on channels 12 and up by default due to region settings.  Could you try changing your router to operate on channel 1 or 6?  Your wireless card is definitely able to see these channels.

It's also possible that your router is operating in a mode that Ubuntu can't see.  11g is probably the most likely to be recognized; can you make sure it's on that?

FYI: in most cases, you can configure your router by going to a computer that is connected to it, opening a web browser, and putting '192.168.1.1' in the address bar (if that doesn't work, try '192.168.0.1' or '10.0.0.1').  If it asks for a password, check the outside of your router for the default credentials.

---

### Post by AkuTenshi on 2008-12-23
Thanks! Changing the wireless to channel 6 made it visible.

---

