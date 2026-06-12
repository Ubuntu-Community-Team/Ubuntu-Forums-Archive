---
title: "wireless networks not showing up"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by xieon on 2010-10-17
I have ubuntu 10.10, and at my house I primarily used wired, and it works fine, and under windows earlier today I was able to locate networks, so my wireless card is working.

I'm currently at my girlfriends house, and trying to connect to her wireless internet. When I try to connect, I can't find any networks. I've made sure her network has sharing and discovery enabled, however in my wirelss manager it comes up as blank.

There's the option to add wireless manually, but do I really need to go through the trouble of finding the routers mac address and all that, it should just show up?

Any thoughts as to why this is like this? I could switch back to windows to see if I can connect, but I'm almost positive it's just the linux wireless manager..

---

### Post by Megaptera on 2010-10-17
If it's a Dell laptop, have you tried this:

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

works on Dell laptops as well as 'Mini'.

---

### Post by xieon on 2010-10-17
> **Megaptera said:**
> If it's a Dell laptop, have you tried this:

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

works on Dell laptops as well as 'Mini'.

I  have tried this, nd do have a fell d620, and it didn't help.

also, the card is working, and there are networks showing up in the terminal however not in the maager so i cant connect to them, heres the output of 
sudo iwlist scanning
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

xieon@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:D9:93:84
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"riverside"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000349df7956
                    Extra: Last beacon: 1700ms ago
                    IE: Unknown: 0009726976657273696465
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1603051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B2D993841021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: 00:23:69:62:0E:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Ludens"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005acd9275e30
                    Extra: Last beacon: 1600ms ago
                    IE: Unknown: 00064C7564656E73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010E1BBB2B46DFCC171F1E62F77679A8C9A102100074C696E6B73797310230006526F757465721024000857525435344753321042000C43555130314A3330313930311054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F5000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1A:70:FE:31:F7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"@Home123M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030de7797183
                    Extra: Last beacon: 1632ms ago
                    IE: Unknown: 000940486F6D653132334D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020017
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:26:62:EB:50:04
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DWER1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000030de77b0181
                    Extra: Last beacon: 1580ms ago
                    IE: Unknown: 00054457455231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 05 - Address: 00:26:62:F0:72:70
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"NikkiNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000de4d9f306
                    Extra: Last beacon: 1556ms ago
                    IE: Unknown: 00084E696B6B694E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 06 - Address: 00:26:62:EB:9C:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"LKTQ1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000030de7baba22
                    Extra: Last beacon: 1552ms ago
                    IE: Unknown: 00054C4B545131
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 07 - Address: 00:18:4D:9C:5A:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"TAZNBILL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043cd5737e5
                    Extra: Last beacon: 1552ms ago
                    IE: Unknown: 000854415A4E42494C4C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by xieon on 2010-10-17
well I finally got it working, i'm not sure what it was that actually fixed it, and i did a ton of commands just one after another, so not sure what helped the best.

i would guess that wicd was the thing that actually caused the fix. More can be read here
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
and it's easy to install by
```
 sudo apt-get install wicd

```
after i installed that i opened the wicd interface, which showed all the wireless connections, then when i looked at the regular ubuntu 10.10 manager, it had changed, and now was displaying all the networks, and allowing me to connect to them

this may had been all i needed, but I also did these things, which may or may not help
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
sudu rmmod -f dell_laptop

```
The above three codes, in order, updated the repositories, updated the broadcom drivers, and the last was something for dell laptops, which i have (dell latitite d620)
and lastly, I installed a driver set that uses windows drivers, its nidswrapper, which can be found in the software center easily.


This was frustrating as hell to find a simple answer, but no really complicated steps, hopefully someone else can get an easy fix w/o having to search forever to find a simple solution

---

### Post by Megaptera on 2010-10-17
Well done on solving it!!

---

