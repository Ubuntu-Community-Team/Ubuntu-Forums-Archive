---
title: "Quantzal - wireless light turn off was working now not?"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by xtextedx on 2013-01-11
Hi,

When I upgraded to Quantzal or 12.10 I found that you had fix the issue with the light on my laptop not turning off when bluetooth and wireless was off. But in the last say 3 days It is stuck on and doesn't want to turn off - this does not seem to affect the operation of wireless or bluetooth but as a precaution, 
I blacklist the drivers.  in /etc/modprobe.d/blacklist.conf

blacklist uvcvideo
blacklist btusb
blacklist bluetooth
blacklist rfcomm
blacklist bnep
blacklist iwlwifi
blacklist mac80211
blacklist cfg80211

I am running.
 
uname -a
Linux 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I would love to get it working again if someone could help me :D
I just dont know where to start?

---

