---
title: "(Xubuntu 11.10) ASUS USB-N13 card problem"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by Ta183 on 2012-03-18
I recently purchased an Asus USB-N13 USB wifi dongle to throw on my old PC, which I was putting Xubuntu on. Everything I read said it would work out of the box. Well, it does, but at 40kb/s and my speedtest chart looks like a saw. It connects at 40kb/s download speed for a few seconds, then nothing for at least ten, then back to a measely 40kb/s. I've tried searching google for an asnwer but everything is for older versions of Ubuntu or fragmented all to heck. I can't get a concrete answer. Interestingly enough, I tested the stick in WinXP on this machine before I installed Xubuntu and I was getting the full 11-16mbit/s I was expecting.  It seems to be using the ra2800 driver. I'd install the newer linux driver on the disc, but I've been using linux for a little under a month and it reads like a foreign language. Also, it only seems to work in the first USB port I plugged it into. I want to move it to the back but I get no traffic when it's there. It connects to the network but no internet.

---

### Post by chili555 on 2012-03-19
I notice Ralink has a newer firmware on their website; I've attached it here. Please download it to your desktop. Right-click it and select *Extract Here*. Now open a terminal and let's back up your current firmware:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
```Now we copy over the newer firmware:```
sudo cp Desktop/RT2870_Firmware_V22/rt2870.bin /lib/firmware
```Now unload and reload the driver:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Any improvements?

---

### Post by Ta183 on 2012-03-19
No, it does not seem to have changed.

---

### Post by chili555 on 2012-03-19
I am aware that this driver has difficulty with N speeds. Is your router set up for B, G and N or B and G only? Can you change it? What does this tell us:```
sudo iwlist wlan0 scan
```

---

### Post by Ta183 on 2012-03-19
I'm not sure about the router. I can't do anything about it, it's not under my control. If it's the problem I'll put in a request. There are three or four routers in the house, anyway.
```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:CA:21:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"38-Super"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c1954dfaad
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000833382D5375706572
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AFE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33FE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070500000000000000000000000000000000000000
                    IE: Unknown: DD940050F204104A0001101044000102103B000103104700102880288028801880A8800014D1CA21281021001C552D4D6564696120436F6D6D756E69636174696F6E732C20496E632E1023000E552D4D6564696120446576696365102400064465766963651042000831323334353637381054000800060050F20400011011000A552D4D65646961415053100800020084103C000101
          Cell 02 - Address: E6:91:F5:B0:F8:49
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"38Special"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b74b8fc04
                    Extra: Last beacon: 1596ms ago
                    IE: Unknown: 000933385370656369616C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
          Cell 03 - Address: 00:18:E7:E7:E4:86
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"CATHERINE-PC_Network_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f9c971599
                    Extra: Last beacon: 1536ms ago
                    IE: Unknown: 0016434154484552494E452D50435F4E6574776F726B5F31
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160300190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340300010000000F000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010A1742FD6DB74338B81FB3843403F660A1021000E442D4C696E6B2053797374656D73102300074449522D363238102400024132104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020084
          Cell 04 - Address: E0:91:F5:B0:F8:49
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Coonan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b74b8d604
                    Extra: Last beacon: 1604ms ago
                    IE: Unknown: 0006436F6F6E616E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B0001031047001000000000000010000000E091F5B0F849102100074E65746765617210230008574E445233373030102400025631104200046E6F6E651054000800060050F204000110110008574E445233373030100800020086103C000103
          Cell 05 - Address: 78:CD:8E:D2:BB:90
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SUDDENLINK.NET-BB8D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c194801162
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 001353554444454E4C494E4B2E4E45542D42423844
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000F127A
                    IE: Unknown: DD07000C4304000000

```

---

