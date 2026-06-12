---
title: "wireless device is disabled"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by siva_ on 2009-01-05
I have a USB wifi device attached by my kubuntu 8.10 setup. When I run iwconfig the device is recognized. When I run iwlist ra0 scan it successfully returns the SSIDs from my local area, including my wifi router.

The problem is knetworkmanager tool doesn't allow me to create a new connection using this device. When I right click on it it says "ra0 wireless is disabled". 

I tried to create a new connection and choose that device, but the SSIDs don't show up in the list. 

How can I configure my wireless through the console, or how can I get knetworkmanager to let me create a connection with this device?

Thanks

---

### Post by siva_ on 2009-01-05
I'm reading the wifi docs found here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection)

When I try to do this:
sudo iwconfig <ath0> essid <essid> ap <xx:xx:xx:xx:xx:> key <XXX> mode <> commit

using my settings, I get an error message like:
SET failed on device ra0 : operation not permitted

I tried it as sudo, but that doesn't seem to affect it.

---

