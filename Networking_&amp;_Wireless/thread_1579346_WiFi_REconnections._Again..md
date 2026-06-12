---
title: "WiFi REconnections. Again."
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by ilna on 2010-09-21
Hi!

I'm running WiFi AP (hostapd/nl80211) and STA (Wicd) in my home net. More or less all does work fine at last. The only problem I have - STA reconnection works few times only (1-4 times), ending with unsuccessful authentification (and multiple AP probing in hostapd debug output before STA failing).

Two contradictive facts take place:

1. Reloading hostapd on the AP side permits Wicd to reconnect, while STA rebooting(!) doesn't help.

2. Another STA - my son's Nokia mobile phone (don't know a model) - reconnects with this AP without problems (we have tried 10 times).

So, you see, first fact says something wrong with AP, while the second one says something wrong with STA. Or you can treat these facts in strictly opposite way :)

Indeed WiFi under Linux is very fragile area yet. I have found plenty of close-to-be-similar reports as well as different resolving ways (but it is rare case).

OK, few words about setup. Up to date Kubuntu Maverick testing with backports enabled on both sides. ASUS USB-N11 adapters are in use on both sides. It means RT2870 chip.

Already have tried:

- hostapd from git,
- compat-wireless 2.6.35-1,
- and plenty of configuration settings.

.. with the same "very stable effect" :)

Thoughts?

---

### Post by ilna on 2010-09-22
ping

---

