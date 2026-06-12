---
title: "Wifi Master mode unstable with RT61"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Punkoff on 2010-03-02
I'm trying to set up a wireless AP using the D-Link DWA510 802.11g card.
I've got hostapd running and the stuff works, but very unstable. This means, connection is estabilished 1 out of 3 times, and is lost after 5 minutes.
When running hostapd with -dd option, I'm getting following when client tries to connect:


IEEE 802.11: authentication ok (aid 1)
IEEE 802.11: did not acknowledge association response


And then client hangs and tries to connect forever.
I've also built the upstream hostapd, but no difference.
Also, tried building serialmonkey rt2x00 drivers from source, no effect.

The configuration:
AP:
Ubuntu 9.10 server @ 2.6.31-14-generic
D-Link DWA-510 802.11bg rev. B card running rt61pci driver.
hostapd 0.6.9 using nl80211

Client:
Ubuntu 9.10 @ 2.6.32-14-generic
Atheros Communications Atheros AR8121

---

