---
title: "Ignoring unknown interface wlan0=wlan0"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Dunhausen on 2010-06-06
Also having this problem on Ubuntu 10.04.

If I do "iwlist scan" I can pick up networks on wlan0:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:F7:3B:52
                    ESSID:"honeypot"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

But if I try "ifup wlan0":
```
Ignoring unknown interface wlan0=wlan0.
```

So far neither of my cards which worked in Ubuntu 8.04 work in 10.04.  The windows drivers apparently do work, except of course for that it's not possible to bring up the interface. :(

---

### Post by Iowan on 2010-06-06
Moved from [year-old thread]("http://ubuntuforums.org/showthread.php?p=9419786") to it's own.

---

### Post by chili555 on 2010-06-06
As far as I know, *ifup* calls up interfaces listed in /etc/network/interfaces. Interfaces controlled by Network Manager are not. Can you click the NM icon and connect?

---

