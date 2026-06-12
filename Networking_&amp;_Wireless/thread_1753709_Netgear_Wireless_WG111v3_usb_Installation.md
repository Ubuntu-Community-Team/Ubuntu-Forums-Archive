---
title: "Netgear Wireless WG111v3 usb Installation"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by nathan soulfly on 2011-05-09
Hi i m new to ubuntu.I have recently move near my sister home and my INTERNET haven't been moved  yet to my new home ,so now i connect to the Internet with a wireless tplink usb (which works fine with no installation needed) on my sisters netgear DGB111G modem.this modem came with a wireless usb WG111v3.I tried to install it based on some threads on this particular wireless usb but still i can make it work.To day i took for my sis the installation cd tried but nothing again.With the WG111v3 i hope to have better wireless signal.

help!!!

Thank you in advance

---

### Post by Jake.Debord on 2011-05-09
Please use terminal and post the results of 

> iwlist

---

### Post by josephmills on 2011-05-09
i think that jake meant ```
iwlist scan
``` I could be wrong though

---

### Post by Jake.Debord on 2011-05-09
Your right, it's Monday :)

---

### Post by nathan soulfly on 2011-05-09
soulfly@soulfly-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:32:F6:E4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041f551c3ac
                    Extra: Last beacon: 864920ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00
                    IE: Unknown: DD890050F204104A00011010440001011041000100103B00010310470010B12FD56729C2921930C53BCAD2DD912A102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086

soulfly@soulfly-desktop:~$

---

### Post by Jake.Debord on 2011-05-09
It looks like the USB adapter installed correctly... I guess your problem is connecting to a network? Download WifiRadar, that is what I use and worked like a charm.

[http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html](http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html)

---

### Post by nathan soulfly on 2011-05-09
really i dont know is happening.i already have wifi radar.i just pluged the usb and it worked without using wifi radar!!!before it had signal like 4 bars but it would say disconnected and its connect but only one bar.it s making me crazy.i cant wait to have my internet connection moved her.modem priceless.



thanks

---

