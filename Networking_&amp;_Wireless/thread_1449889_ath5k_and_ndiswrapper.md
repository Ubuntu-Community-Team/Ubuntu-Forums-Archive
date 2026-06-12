---
title: "ath5k and ndiswrapper"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by mark bower on 2010-04-08
I am trying to get my Netgear WPN311 pci card with Atheros AR5001X+ working, only this one card installed.  It sees my AP, but it will not connect when I select it. It is my understanding that 9.10 has the ath5k driver in the kernel, thus the WPN311 should work out of the box. I have ndiswrapper installed with a driver for use by another card - this set-up works just fine.  

1) Does ndiswrapper have to be disabled for the ath5k driver to work?
2) If ndiswrapper does have to be disabled, can I do it without deleting it in Sys>Admin>Windows Wireless Drivers so that I can reenable it if I do not get the WPN311 working?  That is, how to disable and reenable, not delete and reinstall if possible.

mark

---

### Post by mark bower on 2010-04-08
SOLVED.  The Netgear WPN311 that I purchased online "works out of the box".

I use MAC address filtering for security.  I forgot to enter MAC address for wireless card at router.  I removed ndiswrapper and driver for other card - may not have had to do so?

---

### Post by mark bower on 2010-04-09
disregard

---

