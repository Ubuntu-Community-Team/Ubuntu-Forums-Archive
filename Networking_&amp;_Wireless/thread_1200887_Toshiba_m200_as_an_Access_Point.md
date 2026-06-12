---
title: "Toshiba m200 as an Access Point"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by twinotter on 2009-06-30
hi,

ubuntu version 9.04.

I'd like to use my toshiba m200 as a wireless access point.  I'm not having any luck either connecting to it through network manager, wicd, or hostapd - though I'm not convinced I've done the setup correct for any of these...

First, I have a AWUS036H that I managed to get working correctly.  The default mac80211 drivers gave me sporadic results and low signal strength.  I blacklisted them and installed the ieee80211 drivers and it seems to work fine - even through network manager, which was unexpected.

I'd like to use the internal wifi card (Intel Pro/Wireless LAN 2100 3B Mini PCI Adapter) as the access point.  I'm missing some base information though to get this working...

First, it seems like actually getting it running in Master mode and using WPA encryption requires using the hostapd application.  Is this correct?  Are there other ways to make this work?

hostapd doesn't seem to support ieee80211 drivers.  I'm unsure, but it seems like the 2100 is no longer using the mac drivers, but the ieee drivers.  I'm basing this on this line from an lsmod, since I didn't see any operational difference when I switched:

ieee80211     38344   1   ipw2100

From there, I'm drawing a blank.  Any direction (even useful search terms) would be great.

Thank you,
twinotter

---

