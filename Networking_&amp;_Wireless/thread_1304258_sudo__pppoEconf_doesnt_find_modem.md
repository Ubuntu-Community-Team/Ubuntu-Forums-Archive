---
title: "sudo  pppoEconf doesnt find modem"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by ubiubi on 2009-10-29
Hello all

I recently changed my service provider to SFR and they sent me their 'neufbox' modem. This modem is also a router with connections for several computers. This modem installed flawlessly in XP (With their CD) but not in 8.10 Beta. I tried The pppoEconf command which had worked with my 'Orange' modem (ADSL) but it identifies 'etho' and 'vbox....' at the beginning of the process then finally finishes with the message 'Access concentrator of your provider did not respond.......another running pppoe precess may be responsible .....' I ran 'poff dsl-provider' in a terminal and ran'pppoeconf' again. 

The same result!


I'm at a loss, all the buttons are illuminated on the modem (like on XP -I have a dual-boot system) except that the 'traffic' light flashes, which should be illuminated if connected.

Any suggetions ???:(

Thanks to all

---

### Post by ubiubi on 2009-11-04
SOLVED

I reinstalled Karmic and it worked upon start up, with no intervention whatsoever!

---

