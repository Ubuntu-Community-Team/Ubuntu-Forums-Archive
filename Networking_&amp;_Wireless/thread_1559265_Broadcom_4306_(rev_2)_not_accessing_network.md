---
title: "Broadcom 4306 (rev 2) not accessing network"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2010-08-23
With the help of the package b3-fwcutter I can scan and see that there are wifi networks available but not connect.  


```
$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"mini"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001367f818c
                    Extra: Last beacon: 188ms ago

```


dhclient does not connect to them

What must be changed to use the aged broadcom 4306 with kubuntu 10.4 with a network it can detect?

---

### Post by Lars Noodén on 2010-08-26
b3-fwcutter figured in the solution.  802.11b and 802.11g now work witj that card.

---

