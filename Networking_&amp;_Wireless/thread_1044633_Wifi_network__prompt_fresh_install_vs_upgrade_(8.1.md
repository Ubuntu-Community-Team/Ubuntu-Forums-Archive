---
title: "Wifi network  prompt fresh install vs upgrade (8.10)"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by gmarton on 2009-01-19
nm-applet does not work with wireless.

I have configured wireless connection in /etc/network/interfaces works fine if I do a manual ifup ethX.

However it does not show in network applet.

This has worked fine on a fresh install of 8.10 but not upgraded one. Fresh install prompts if wifi network is available. 

I tried apt-get purge network-manager-gnome but no dice.

Anyone had this happen before?

---

### Post by gmarton on 2009-01-19
in /etc/NetworkManager/nm-system-settings.conf set
managed=true

then 

sudo killall nm-system-settings

now I see wireless in nm-applet.

---

