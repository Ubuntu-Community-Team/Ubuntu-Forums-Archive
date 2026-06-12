---
title: "The problem may not be your Ubuntu or wireless adapter."
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by oblong on 2012-08-03
I recently has a strange problem with 12.04 Precise. The problem occurred with various wireless adapters, both USB and PCI express. All were various Atheros devices (currently AR9287 - TP-Link TL-WN881D). Some 802.11g. Others 802.11n.

All connected out-of-the-box.

As the machine is for MythTV, it was configured for access from other computers (for Mythweb, etc). Everything was fine with wired Ethernet before moving to wireless. That was fine initially, too.

However, I noticed that after some time (between half an hour and an hour), I could no longer access the wireless MythTV machine from other computers (even pinging would not work). 

Oddly, the MythTV box itself was still happily talking to the Internet, and could ping other PCs.

Especially bad was pinging wirelessly from my smartphone, with many dropped packets etc. It had no problem pinging wired computers.

Restarting the MythTV wireless connection made things work again.

So after much searching, suspecting the devices and/or drivers etc, I thought that perhaps there was a problem with the common device: the wireless router (Billion 7404VGP).

So I hooked up another router to do the wireless function for my network, and everything then worked!

No more "timeouts", or bad pings.

Another clue (mainly in retrospect) is that when I tried to FTP to my smartphone from my wired PC, I had to turn off the phone's wireless for a couple of seconds, then on again before it would connect. Now it connects first time.

Hope this helps someone, and that I have not missed something else entirely!

---

