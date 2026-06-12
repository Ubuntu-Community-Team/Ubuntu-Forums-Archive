---
title: "Insane WLAN lag spikes: How-to-fix"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by SRTS on 2009-11-05
Toshiba Satellite A200-12F, Atheros 5001 Wifi.

Issue 1)
--------
I noticed that Ubuntu 9.10 broke my WLAN out of the box:
After installing, it had somehow set my eth0 (which I don't use) as default adapter, and was trying to DNS through it, so I didn't get any name resolution, and 'route' command took like 10 s to complete oO.

After installing wicd, which connected/disconnected in 3 second intervals (during which I could however ping stuff if I was quick enough!) I switched back to gnome network-manager, and suddenly DNS and correct default route worked!

Issue 2)
--------
However, connection was terribly laggy, totally unbearable. Every minute I'd have a 20 second lag spike etc.
So I tried two things I found on the forums and after some googling in different places:

a) disable IPv6. This had no effect at all.
b) get 'madwifi' code from the madwifi homepage, specifically version 0.9.4, compile and install it. Remove blacklist-flag from 'ath_pci' driver in /etc/modprobe.d/ (which is the madwifi thingy) and instead blacklist ath5k (and ath9k just to be safe) which is the broken laggy default driver. You might have to type 'sudo insmod ath_pci' to enable the driver, but I think it's probably not required.
After a restart, everything works perfectly!!
Awesome WLAN performance and no lags at all now.


I wonder why the Ubuntu dudes appearently completely removed the working madwifi driver from the repository, requiring people to compile stuff to fix 9.10. And what's up with the broken DNS/route things right out of the box?? I don't get those people at all, making me waste hours of spare time for frigging troubleshooting.

Hope this could help you too, if you have similar troubles.

---

