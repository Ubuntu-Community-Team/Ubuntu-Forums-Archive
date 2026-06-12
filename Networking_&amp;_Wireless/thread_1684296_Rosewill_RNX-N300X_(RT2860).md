---
title: "Rosewill RNX-N300X (RT2860)"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by gstilma on 2011-02-08
This is a problem thoroughly discussed [here]("http://ubuntuforums.org/showthread.php?t=1476007"), [here]("http://ubuntuforums.org/showthread.php?p=9289963"), and elsewhere, but I still need help.

I have a Rosewill RNX-N300X PCI Wireless card (which uses the Ralink 2860 chipset). When I installed it in 10.04, the first fix above to update & modify the drivers worked like a charm.

Now, I've just built a new system and freshly installed 10.10 64-bit, but can't get the wireless card to go above 54 Mb/s, which is pretty lame compared to the 270 Mb/s I was getting before. Neither of the above fixes work for me. The first one that worked before might not work now because the Ralinktech drivers could be just 32-bit. The second solution uses ndiswrapper and includes some notes for 64-bit drivers, but still no luck.

What seems to be the problem is that Network Manager is stuck using the 'rt2800pci' driver. Any thoughts on how to get me back up to 802.11n speed?

---

### Post by gstilma on 2011-02-08
Solved. The old `4th time's a charm' solution is what worked. Sorry for the extraneous post, moderators.

---

