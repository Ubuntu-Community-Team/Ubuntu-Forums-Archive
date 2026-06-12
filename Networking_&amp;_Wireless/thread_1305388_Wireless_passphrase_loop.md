---
title: "Wireless passphrase loop"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2009-10-29
It seems that in 9.10 when I try using my usb wireless it goes into an endless loop of asking for my passphrase. It never actually connects, but keeps trying to. I wanted to know if there was something I was forgetting, but I don't think I ran into this problem when I installed 9.04 a while back. Also, my card is a d-link dwa-140 usb adapter(Ralink 802.11n adapter).

---

### Post by brandon88tube on 2009-10-30
Nothing? I realize its a new release so there are tons of people on the forums complaining and I see a ton of wireless stuff, but so far not much that matches up with mine...though I haven't looked that hard so don't quote me on that.

---

### Post by chaosmosis on 2009-10-30
I have the same issue and am still having a hard time finding a solution with ubuntu 9.10 and a d-link dwa-160. Network manager tries to connect but get pop-up w/passphrase dialog.

---

### Post by JBAlaska on 2009-10-30
Is that the RT2870 chipset? If so installing the latest driver off the Ralink site and blacklisting the 9.10 driver worked great for me with my Linksys WUSB600N.

This [Post](http://ubunturt2870.pbworks.com/FrontPage) is the one that finally got it working for me

---

### Post by Eric Lathrop on 2009-10-30
I had the same problem with my Atheros based card.
I got a basic connection working by:

[LIST=1]
[*]edit /etc/modprobe.d/blacklist-ath_pci.conf
[*]comment out the blacklist line
[*]reboot
[/LIST]
Although I'm still experiencing really slow speeds, and constant reset connections (but the wifi connection to the AP is solid the whole time)

Any ideas?

---

