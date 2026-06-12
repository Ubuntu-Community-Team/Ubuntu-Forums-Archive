---
title: "Wireless missing"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by olympic on 2012-06-03
I have an odd situation with my Ubuntu 12.04 installation.

It has been working quite happily since I did the upgrade from 11.10 until this morning when I find I have no wireless network connection available.  The computer is a dual boot with Win 7 and wireless works on that O/S.  There are only minimal options available when I click on the network connection icon on the top panel, one of which say "Wireless Network:  Diconnected" (greyed out)but my wireless hardware switch is "on" and the indicator is alight.

I decided to change the hard drive for one which has the same configuration (dual boot Ubuntu 12.04 and Win 7, and Wireless works with Ubuntu on that hard drive.  Driver listed under "Connection Information" is "ath9k".

Computer is a Sony Vaio laptop, 320Gb HD with 4Gb RAM.

Any thoughts?

---

### Post by olympic on 2012-06-03
Problem solved - sudo rfkill unblock all.

---

