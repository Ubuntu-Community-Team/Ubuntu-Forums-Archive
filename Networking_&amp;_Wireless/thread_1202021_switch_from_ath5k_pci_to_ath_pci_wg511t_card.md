---
title: "switch from ath5k_pci to ath_pci wg511t card"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by daggerx on 2009-07-01
Can I do that?

Im running a [netgear]("http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG511T.aspx") card and its running at 1mbps with this ath5k_pci, on my wife's machine it runs 24mbps and up with the ath_pci.

Is there a way for me to switch the default to this ath_pci? Please help and thanks in advance.

---

### Post by t0mppa on 2009-07-01
Sure there is. For instance you can find ath_pci from the System / Administration / Hardware Drivers, it might go under the name Madwifi, but enabling that one should do all the hard work for you.

If that doesn't work, it isn't all too hard to do it manually either, still it's easiest to try the automated way first.

Oh and if you only get 1 Mb/s bit rate in iwconfig, you can try using **sudo iwconfig wlan0 rate 54M** for instance to get 802.11G speeds without having to reinstall drivers or anything.

---

### Post by daggerx on 2009-07-01
Thank you so much. Funny thing is I did it for my wife and I forgot and I got the card today...Thank you again....for the quick response.

---

### Post by t0mppa on 2009-07-01
No problem, glad to see you got it working. You might want to write down what you did this time though, in case you forget it again. :)

---

