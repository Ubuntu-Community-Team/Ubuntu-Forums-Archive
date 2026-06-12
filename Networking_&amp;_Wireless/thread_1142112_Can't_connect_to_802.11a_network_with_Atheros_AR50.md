---
title: "Can't connect to 802.11a network with Atheros AR5004X in Jaunty"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by bungee_70 on 2009-04-28
Hi, 

I just upgraded from Hardy to Jaunty and now I can't connect to my 802.11a network anymore. Strangely, I managed to connect once after several failed attempts and now I can't anymore.

I have a Belkin AR5004X wireless card (dual-band). I use the ath5k driver. I tried Madwifi without success.

The card is well recognized in the UI, however, my network is showed to have a very weak signal, even if I'm at a couple of feet from it. It loops asking for the password forever. My other Windows computers have no problem connecting to the network with the same card.

Any help appreciated. Thanks!

---

### Post by bungee_70 on 2009-05-09
It seems that the problem may be that my router is 108mbps only and the linux driver tops at 54mbps. Is there a way to have Super A speed in Linux?

---

### Post by bungee_70 on 2009-05-09
Well, I set my router to disable 108 and it changed nothing on Linux...

---

