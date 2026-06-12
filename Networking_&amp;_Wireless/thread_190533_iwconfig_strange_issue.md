---
title: "iwconfig strange issue"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Cenotaph on 2006-06-06
Im trying to configure the access to my university WLAN, but whenever I type "sudo iwconfig eth0 essid e-U enc open"

it gives me an invalid argument error Set Encode (8B2A). The error seems to be in the "open" but why, it was supposed to recnogize it, no?

thanks in advance

---

### Post by Cenotaph on 2006-06-06
If i use the bcm43xx driver the command seems to work, but wpa_supplicant apparently doesnt support that driver, so i cant configure the network anyway :(

im using ndiswrapper.

so, i have two alternatives.

either i get ndiswrapper to support that command. or i get bcm43xx getting to work with wpa_supplicant. Network Manager frontend won't do... :(

---

