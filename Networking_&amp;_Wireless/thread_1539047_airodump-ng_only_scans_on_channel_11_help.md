---
title: "airodump-ng only scans on channel 11 help"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by bklynghost on 2010-07-26
i just installed ubuntu 10.04 on my computer, and tried to airodump, but noticed that its stuck on 11th channel, when i specified only channel 6 during scan, it gave me hosts from channel 6 and 11, but then i ran aireplay-ng and it runs on 11th channel as well, even when i put my card into monitor mode with a specific channel option. btw my chipset is AR9285 with ath9k driver.
everything worked in backtrack.
i also tried to reinstall aircrack which did not work.

---

### Post by eliwis on 2010-11-20
Hi, 
One thing that comes to mind is that you should make sure you aren't connected to a WiFi network while running airodump.
I think that you might be connected to some other wireless network that is broadcasting on channel 11. and that is why your wireless card isn't moving away from it.

---

