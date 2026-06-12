---
title: "USB dongle supporting AP mode?"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by BkkBonanza on 2009-03-24
I'd like to run hostapd on my laptop.
Has anyone found a USB dongle that actually works with Ubuntu and you've tested to work in AP mode? 
I'd go buy one if I know it works. 
If you have done this can you indicate make, model, revision tested.
Thanks!

---

### Post by qduaty on 2009-04-25
rt73 chip is known to work, at least with ubuntu 8.10, kernel 2.6.27-10, "compat-wireless" driver set and hostapd 0.6.6. Hostapd often rejects connections with an error which is actually ******** ("did not acknowledge authentication response"), so you may have to disable it in source code.

WPA2 works, but has problems with authentication on some stations.

---

### Post by BkkBonanza on 2009-04-25
Thanks for the info.

I had already bought an Atheros (ath9k) mini PCIe card to replace the internal Intel card. This has worked well with hostapd - although I find the receive senitivity lower than the Intel one. I'm not sure why that is or if it will improve as the driver matures.

I've also got a Broadcom 4311 card coming in the mail to try out. Just want to see if it does better and it was quite cheap, $14 inc. shpg.

---

