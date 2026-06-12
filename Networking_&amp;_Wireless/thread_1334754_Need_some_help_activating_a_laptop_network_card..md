---
title: "Need some help activating a laptop network card."
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Ruskiy Letenant on 2009-11-22
I just installed Ubuntu 9.10 and realised that I cannot connect to the Internet via my wireless card. I'm on wired LAN right now, and want to make the wireless work. No clue here, can anyone help?

I have searched some other threads that suggested installing ndiswrapper, but it stopped at 5%, then boosted to 50% after about an hour and just gave an error message. Need some other options.

My wireless card is [B]Broadcom Corporation BCM4311 802.11b/g WLAN.


[/B]

---

### Post by coffeeaddict22 on 2009-11-22
Hi,
Look in System/Administration/Hardware Drivers and if it's there, enable the Broadcom STA driver.  If it's an option, it's by far the simplest.

---

### Post by Ruskiy Letenant on 2009-11-22
That was by far the simplest, most unexpected way of fixing this here problem.

Thank You so much. ):P

---

### Post by coffeeaddict22 on 2009-11-22
No prob.  Everyone groans about it, but it's hidden on purpose.  Broadcom won't release the source code for their drivers, so there's a blob of binary in there that nobody's 100% sure about.  That goes against the underlying principles of open source software, so there has to be an explicit choice to install it.

Why a hardware company won't let people know how to (digitally) talk to their product is completely beyond me.  Maybe for some of the population, secrecy is good; another theory is that they're too embarrassed at the quality of the software.

---

### Post by Ruskiy Letenant on 2009-11-24
Some companies are just like that, but good point, they aren't a top ranking company and perhaps they really are embarrassed of the goods, only makes people dig deeper and find out the reality...seems they would be better off releasing the full instead of withholding what they do. :D

---

