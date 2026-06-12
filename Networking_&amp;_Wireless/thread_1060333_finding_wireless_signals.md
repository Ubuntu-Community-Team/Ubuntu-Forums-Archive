---
title: "finding wireless signals"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by AutumnPhoenix on 2009-02-04
Hey, I have friendly neighbors all of whom don't care if I share wireless.  I seem to connect only to one, however, and its not the strongest connection.

I use the terminal "dhclient" command, I've also tried dhclient ath0 and iwconfing 

Is there another command I can try?

---

### Post by chili555 on 2009-02-04
Do a scan to determine which networks are available:```
sudo iwlist ath0 scan
```You might see something like:>  Cell 01 - Address: 00:12:0E:46:0C:76
                    ESSID:"WEST5214"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a540343eba
                    Extra: Last beacon: 3308ms ago

          Cell 02 - Address: 00:1C:DF:52:0B:5E
                    ESSID:"Dynex"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=73/100  Signal level:-87 dBm  Noise level=-88 dBm
                    Encryption key:off
Now let's tell *iwconfig *that we explicitly want the stronger of the two, in my example, *Dynex:*```
sudo iwconfig ath0 essid Dynex
sudo dhclient ath0
```Did you connect to the correct access point?

---

