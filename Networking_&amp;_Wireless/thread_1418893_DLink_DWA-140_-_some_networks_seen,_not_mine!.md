---
title: "DLink DWA-140 - some networks seen, not mine!"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2010-03-01
Hi,

I've just bought a wireless USB stick in an effort to get better range and speed than my old PCI 802.11G card.

The stick is detected OK, and appears as "Wireless Networks (Ralink 802.11 n WLAN)" when I left click on the wireless network strength notifier.

However it doesn't list my house network! I know the network is in range because I'm accessing it now through my old PCI card. I've also had the Dlink USB adapter work fine through Windows XP, with signal strength somewhere near 70%.

Networks that are listed (neighbours) are _all_ shown at 100%, which is a little suspicious.

If it helps, the stick is hardware version B1, firmware version 1.20(E).

So how can I get this adapter to pick up my home network?

Thanks for any help / advice.

---

### Post by ciaopaulo on 2010-03-01
Problem fixed with tips given [here]("http://swiss.ubuntuforums.org/showthread.php?t=1342593").

Ie.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

then add to file:

```

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

---

### Post by davemar on 2010-03-22
That seems to have fixed it, thanks for that!

---

### Post by Jelle_S on 2010-12-08
Just wanted to add that this is a great fix for all those who have problems with a D-Link DWA-140 adapter. I spend hours searching for a solution, this one worked.

---

