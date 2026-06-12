---
title: "TP-Link router only connects to unsecured networks"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by goseph on 2010-06-05
hi all!

I set up my TP-Link TL-WR541G/TL-WR542G wireless today, I am trying to connect my laptop wirelessly.

What works:
- wired connect through the router (does not ask for password)
- wireless connect through the router with no password-encryption

what does not work:
- wireless passworded connection

Interestingly:
- doing an upgrade to the latest 2.6.32 kernel today appears to have fixed the wireless network detection capabilities of my laptop which did not work at all before today
- I originally set a 156-bit password but when I attempted to connect through the default gnome wifi thing it asked me for a 128-bit password. the 156 bit password did not work so I tried setting a 128 bit password in the router but that also failed.

Does anybody have any suggestions or ideas?

*Edit*
I changed a security setting in router configuration from *shared key* to *automatic* and it fixed the problem when in windows XP but not in Lucid Lynx. Perhaps this sheds some light...?

*Edit*
Changing security from WEP to WPA in the router solved the problem!

*Edit*
For some reason, following a reboot, Ubuntu now no longer detects any wireless networks at all... so close (XP detects)

---

