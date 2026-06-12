---
title: "Finding Wireless Router's MAC"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by hanzj on 2012-05-23
Hello,

How can I determine a wireless router's MAC address.

I'm trying wifi-radar, but it is giving the wrong last character of  our router.

---

### Post by chili555 on 2012-05-23
You might try:```
sudo iwlist wlan0 scan
```Here is an example from my system. The MAC has been redacted.> wlan0     Scan completed :
          Cell 01 - [COLOR="Red"]Address: 99:13:10:62:8D:77[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
Don't forget, your router has several different MAC addresses. There is one for the ethernet port through which the router receives the internet, one each for the ethernet ports to which each LAN computer attaches and another for wireless.

---

