---
title: "Getting Edmiax ew7718 to work?"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by diegogranziol@gmail.com on 2009-03-07
Heya guys, i bought the new Edimax Ew7718 with the impression that it wouldn't be too difficult to configure/use under linux, guess i was wrong,lol.

Found the native linux Ralink driver, believe its the Ra2860?
Installed it, with sudo make and make install (didn't see a configure option)

it seemed to install fine
get this when i type sudo iwconfig

> ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


however, i seem to be unable to use it for anything worthwhile, such as scanning for networks or connecting, such as when typing iwlist ra0 scanning

i get

> ra0       No scan results


any ideas on what i could do?
thank-you.

---

### Post by diegogranziol@gmail.com on 2009-03-10
anyone?

---

