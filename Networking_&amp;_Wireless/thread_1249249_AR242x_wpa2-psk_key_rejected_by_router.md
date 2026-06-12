---
title: "AR242x wpa2-psk key rejected by router"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Nephtys on 2009-08-25
I previously had trouble connecting to wifi at all (see [here](http://ubuntuforums.org/showthread.php?t=1231321)), which has now been solved by ndiswrapper and wicd (see [here](http://ubuntuforums.org/showthread.php?t=885847)).

My wireless works on open networks now, but I still cannot connect to my wpa2 secured router because it will not give me an ip address. I checked the router's logs and it indicated that the access attempt failed because the key wasn't correct (yes, I did check that the key *was* indeed correct as I typed it in).

Here's the router's log (in German) and a translation:

> WLAN-Anmeldung ist gescheitert: Autorisierung fehlgeschlagen. Name: <Rechnername>, MAC-Adresse: <MAC-Adresse>.
Eine WLAN-Station hat versucht, sich mit einem ungültigen WLAN-Netzwerkschlüssel anzumelden. Die FRITZ!Box hat die WLAN-Verbindung daher abgelehnt. Die WLAN-Station hatte zu keinem Zeitpunkt die Möglichkeit, Daten mit Ihrem Netzwerk auszutauschen.

WLAN access failed: Authorisation failed. Name and Mac address are indicated here.

A WLAN-station tried to access with an invalid WLAN network key. The Fritz!Box therefore denied the WLAN connection. The WLAN station never had the possibility to exchange data with your network.

```
nephtys@nephtys-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:8A:29:FB
                    ESSID:"Thomson9C294C"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1F:3F:1C:6F:6B
                    ESSID:"FRITZ!Box Fon WLAN 7570 vDSL"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

Any ideas?

---

### Post by Nephtys on 2009-08-27
Bump for attention?

---

### Post by t0mppa on 2009-08-27
Since no one seems to have any bright ideas, here's something worth checking out: how up-to-date are the Windows drivers you're using? I had a similar issue with Ndiswrapper, when I tried it for another card (my ar242x work just fine with the native drivers) and the only reasonable explanation I could find was that the drivers it was wrapping were so old that they didn't support WPA or WPA2 yet, as open & WEP networks worked just fine.

---

### Post by Cuba71 on 2009-08-27
You should try the native driver ath5k, it works fine with my AR242x with WPA & WPA2 Personal

---

### Post by Nephtys on 2009-09-18
I've been through a busy spell there, so I apologize not reacting. Wouldn't want to appear ungrateful. Thanks for the help, I'll give this a whirl.

---

