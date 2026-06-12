---
title: "wifi problem with wpa"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by navaneethan on 2010-12-23
I want to connect wi-fi in my system Past some time it was connectd now it is not connecting

i assume that the problem will be wpa authentication

"
> wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:0C:94:3E
                    Protocol:802.11b/g/n
                    ESSID:""
                    Mode:Managed
                    Channel:6
                    Quality:44/100  Signal level:-72 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported

'


suggest me to connected wi-fi i think every thing is fine;
just it is authenticated with wpa?How to do it

---

### Post by grahammechanical on 2010-12-23
I did not use wireless under Hardy Heron. I cannot take you through the set up in Hardy Heron. 

Basically, to connect to a wireless router/modem that has the encryption key set to on (your one is) you need to enter what is called the wireless key or the WPA-PSK key.

The way it works under 10.10 is to select your wireless network from the list of available networks and when you are asked to authenticate you enter this wireless key. Do not enter your login password. It is usual for this information to be written on a label that is stuck on the bottom of the router/modem. The present network manager will remember this pass phrase or key. It is also possible to put this information into a form but I do not know how to do that under Hardy Heron.

I hope this helps.

Regards.

---

### Post by navaneethan on 2011-01-04
ok..k...I think the problem is with wpa only

---

