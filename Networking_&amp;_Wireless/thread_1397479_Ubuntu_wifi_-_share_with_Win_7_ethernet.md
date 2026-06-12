---
title: "Ubuntu wifi - share with Win 7 ethernet"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by christatedavies on 2010-02-03
Hello. I have Ubuntu 9.10 running on my laptop which has wifi. This connects to the internet through a wireless router - fine.

I have a 2nd PC running Windows 7 with no wireless.

I have connected them using a CAT5 cable, and if I disable wireless networking on Ubuntu, I can copy files between the two of them. But when I re-enable wireless, the wired connection fails.

However, I'd like to set up some sort of passthru - so that the Windows box can access the internet (which is over the wireless of the laptop)

Can someone please guide me in the right direction?

Many thanks, Chris

---

### Post by 2hot6ft2 on 2010-02-03
Internet Connection Sharing
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Also to connect 2 computers by CAT5 at least one of them must have a gigabit (10/100/1000) Ethernet adapter otherwise you will need a **CAT5 crossover cable**. Connecting 2 pc's with a regular CAT5 patch cable when neither of them has a gigabit adapter can damage your equipment.

---

