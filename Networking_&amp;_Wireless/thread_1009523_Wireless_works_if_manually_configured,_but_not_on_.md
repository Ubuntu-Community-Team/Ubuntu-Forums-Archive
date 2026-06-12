---
title: "Wireless works if manually configured, but not on login"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by AlexDavidson on 2008-12-12
Today I moved to a new flat, with Virgin Broadband and a brand new Netgear WGR614 wireless router. Both are working fine.

Unfortunately, my Tablet PC is not. It's an HP Compaq TC4400 hybrid Tablet, running Ubuntu 8.04 and Gnome. For all the bog-standard stuff (ie. the desktop environment the average user expects) it's fairly normal. I can't be bothered fiddling with stuff that works.

What's broken is the wireless. I've noticed a tendency in Ubuntu's network-manager to behave strangely when asked to connect to an encrypted network; specifically, there's no way to force a reconnect when the other end has dropped the connection and n-m hasn't noticed.
More importantly, my wireless settings aren't being saved.

The net result of this is that I'm able to connect via wireless using WEP, WPA, and WPA2 just fine if I do it manually. If I then reboot the machine, all those settings (despite apparently being saved in /etc/network/interfaces) are suddenly ignored. Furthermore, they're ignored in such a fashion that n-m thinks they're in effect, and I have to change a setting and change it back to force a reconnect.

Is this a result of something stupid that I've done, or is it a bug in one of the umpteen bits of software involved? And how do I fix it?

Thanks!

---

### Post by AlexDavidson on 2008-12-12
Fixed it. Gave up trying to enforce anything upon this system and let it use roaming wireless config, then specified that it should automatically load my keyring on login.

Still wondering why it broke under manual config, though.

I really hate 'smart' systems.

---

