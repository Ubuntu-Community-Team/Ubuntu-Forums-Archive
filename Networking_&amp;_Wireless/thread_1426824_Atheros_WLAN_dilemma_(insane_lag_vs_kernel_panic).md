---
title: "Atheros WLAN dilemma (insane lag vs kernel panic)"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by SRTS on 2010-03-10
Ok, I've got a Toshiba A200-12F notebook sporting an Atheros 5001 WLAN.
The trouble with Ubuntu 9.10 is, that I have the choice of using the 'shipped' ath5k driver, or blacklist it and use the madwifi's ath_pci driver instead.

This results in either:

ath5k: InSaNe lags, like every 10-15 seconds network hangs for about a minute.

vs

ath_pci: Network runs pretty decently, except the whole system will kernel panic about every 2 days..


If I didn't have a deeper sympathy for Ubuntu, I would do me a favour and just install an OS that provides proper networking.
However, I'm willing to spend even MORE hours trying to google/compile/fix this crap, if someone would be nice enough to provide any ideas what I could try next....

Also, pretty PLEEEEASE fix it in upcoming Ubuntu 10.4, ok? It's not cool to have no working WLAN in an OS that is neither in alpha-stage nor targetting a niche market or some such.


many thanks in advance
your Ubuntu fan SRTS


PS: I'm strict because I care about it <3

---

### Post by SRTS on 2010-03-11
If this info helps:
If I _do_ use madwifi, as soon as I copy some more data from HDD to USB, the network will sort of freeze, or at least lag so much that I time out. Also, most actions will suddenly take ages, such as opening any kind of application. Like a massive system lag just from some USB copying..

---

### Post by SRTS on 2010-03-19
Well, any solution to the kernel panic yet?
Or, even better, to the ridiculous lags in the DEFAULT installation?

---

