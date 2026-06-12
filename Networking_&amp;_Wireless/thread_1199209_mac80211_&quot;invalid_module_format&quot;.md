---
title: "mac80211 &quot;invalid module format&quot;"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by kartoffel1337 on 2009-06-28
hi,

I have Ubuntu Jaunty with 2.6.28-13 kernel and a intel wifi link 5300 wireless card.
I want to use the newest compat-wireless version from linuxwireless.org.

Compiling is not problem: make, make install, depmod -ae.
But when I try to modprobe iwlagn it tells me that the modules mac80211, iwlcore and iwlagn have invalid module formats.

Any suggestions what's going wrong?
I'm using the same gcc that was used to compile my kernel, so I don't see why it produces incompatible modules.

(I know I can use the backports package to get the card to work, that's no problem)

---

