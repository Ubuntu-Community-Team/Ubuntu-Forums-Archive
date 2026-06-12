---
title: "Madwifi no wifi0 interface"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by mikazo on 2009-04-08
Hey,

I'm having trouble getting my D-Link DWA-643 ExpressCard AR5418 to work. I did it last summer:

[http://mikazotechblog.blogspot.com/2008/08/d-link-dwa-643-expresscard-and-madwifi.html]("http://mikazotechblog.blogspot.com/2008/08/d-link-dwa-643-expresscard-and-madwifi.html")

But now it's not working. I have tried the latest madwifi-trunk, the one from last summer that I used that worked, the ath9k drivers, nothing works.

My problem is that I get a wlan1 interface instead of a wifi0 interface, so I can't wlanconfig to create an ath0 interface because there is no wifi0, if that makes sense.

lsmod | grep ath:
```

ath_pci               216504  0 
wlan                  240368  1 ath_pci
ath_hal               259552  1 ath_pci
ath9k                 274232  0 
mac80211              216820  3 iwlagn,iwlcore,ath9k

```

lspci | grep Ath:
```

04:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
:lolflag

```

And I have ath_pci in /etc/modules and have rebooted and still no luck. Anyone have any ideas? I know there are a lot of threads out there about this, but I haven't found any solutions. Thanks.

---

### Post by mikazo on 2009-04-08
Sorry, found my own mistake. Lingering ath5k modules were the cause of the problem.

I added the following lines to /etc/modprobe.d/blacklist:

blacklist ath9k
blacklist mac80211

Then rebooted, and I have my ath0 interface.

---

