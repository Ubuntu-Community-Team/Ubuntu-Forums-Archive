---
title: "Find all nearby APs with their MAC from terminal"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by johannes_h on 2009-09-20
Hi.
If would like to make a search, for all nearby access points, and their MAC adress. How can I do this from the terminal?

Lets say I wan't to set up iwconfig, and don't know my AP's MAC adress?

Thanks..

---

### Post by chili555 on 2009-09-20
> chili@LAPTOP60:~$ sudo iwlist wlan0 scan
[sudo] password for chili: 
wlan0     Scan completed :
          Cell 01 - Address: [COLOR="Red"]99:24:56:2A:D7:29[/COLOR]
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"XYZ1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
To get *all* the networks in your area may require moving a bit closer to them. For example, upstairs, at the west end of my house, I see three networks. Here, I see only my own. On the front porch, I see 5-6.

---

### Post by johannes_h on 2009-09-20
Thanks alot!

---

