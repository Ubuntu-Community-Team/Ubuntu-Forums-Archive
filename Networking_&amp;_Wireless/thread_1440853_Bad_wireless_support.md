---
title: "Bad wireless support"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by Dalle85 on 2010-03-28
I am tired! Tired of constantly having to fight ubuntu for my wireless connection!

One thing is that Ubuntu (for reasons unknown to even the gods) doesn't support Draft-N on a standard 4965AGN adapter. That I can live with.

I have been running ubuntu for two years now - to begin with, network connection was okay! But with each update, things grew steadily worse! Now, I am forced to using a WEP-security on my wireless because ubuntu won't let me connect to the internet with WPA! 

But even worse, I can't keep a steady connection! Every few minutes, my connection dies causing any active stream to stop and it won't restart unless I refresh the page. This has become such a nuisance that I actually prefer my PS3 for watching video streams (yes, it's that bad)!

I have tried all the tricks in the book - ndiswrapper won't cooperate, filing bugs doesn't help as no one can locate the bug (though I am not the only one suffering) and reinstalling from the beginning doesn't do anything! Wireless (including "N"-support mind you) works flawlessly in Vista on the same computer.

Does anyone know if there is a fix for this? Because I am tired - so tired in fact that I have decided to retire this computer, abandon Ubuntu and buy a MacBookPro if a solution doesn't reveal itself very shortly! I am not going to bother going another round against Ubuntu if I have to keep fighting it - the OS should be aiding me, not fighting me!

The computer is a two year old Acer Aspire 5920g 2.0 Core2Duo with a 4965 wireless adapter.

I am sorry if I seem a little hostile, but as I wrote; I am tired!

---

### Post by xnostradamusx on 2010-03-28
[QUOTE=NightwishFan;9036054]The pefrormance problems on the ath9k driver are fixed install Wireless Kernel Backports.
[Click Here to install..]("apt://linux-backports-modules-wireless-karmic-generic") and press ok to use apturl. Or use:
```
sudo aptitude install linux-backports-modules-wireless-karmic-generic
```

i quoetd nightwish post so i think your using an atheros wireless and this might help

---

