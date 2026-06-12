---
title: "wlanconfig equivalent ath5k command?"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by orangecakez on 2009-03-25
I am using the ath5k driver for my wireless card, and I need to run some "wlanconfig" commands, but those commands are for madwifi drivers. What would be the equivalent command for ath5k drivers?

Like, I have wlan0 and wmaster0 wireless interfaces in ifconfig. How do I make wlan0 completely destroyed instead of ifconfig wlan0 down with the ath5k driver? It would be the madwifi driver equivalent of "wlanconfig wlan0 destroy", Also I'd like to know how to create wlan0 again, which in madwifi one would do "wlanconfig wlan0 create wlandev wmaster0 wlanmode managed". Or something like that (not sure if ath5k has parent mode)

---

