---
title: "After upgrade to karmic only one client can connect to hostapd at a time"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by derjoerg on 2010-02-24
Hi,

I just updated my jaunty-installation to karmic. As a wireless card I have:
```

 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

```

With jaunty I had the ath_pci-module with the following modules-entry
```

options ath_pci autocreate=ap

```

and together with hostapd I was able to have a WPA-secured accesspoint running, where all my wlan-devices can connect to.

Because ath_pci is not available anymore in karmic I checked out the madwifi-sources and compiled them, blacklisted ath5k and re-enabled ath_pci.

So now my accesspoint is back.

BUT ...

as soon as one device is connected and authenticated, a second device will not connect to the AP!!! :confused:

e.g.

As soon as my "standalone internet-radio device" is connected, my laptop will not connect anymore and vice versa. Also in the hostapd-debug-output I see, that the second device "communication" is not listed. :confused: :confused:


Can anybody help?


Thanks in advance

Joerg

---

