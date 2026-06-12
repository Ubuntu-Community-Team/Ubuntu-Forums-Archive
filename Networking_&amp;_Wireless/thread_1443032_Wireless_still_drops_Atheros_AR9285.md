---
title: "Wireless still drops Atheros AR9285"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Djalmahal on 2010-03-30
Hi,

I bought this new computer with an Atheros AR9285 wireless adapter, signal dropped out after a couple of minutes, sometimes reconnected, I looked up different posts on help.ubuntu.com and ubuntuforums.org.

First I installed linux-backports and linux-backports-wireless, still dropped.
Then I installed compat-wireless-2.6.33 and it still dropped.
Finalley I blacklisted the driver with 
gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf
and it still drops.
What should I do, it seems to pick it up again after 30 sec or so, but it a bit frustrating.

Thanks for any advice
Andreas

P.S.: It seems to be getting much better now that I have the torrent program shut down.

---

### Post by Djalmahal on 2010-03-30
It seems to be better now, maybe it just just the local wireless connection, but if you have any feedback let me know

Andreas

---

