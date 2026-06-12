---
title: "Bonding (link aggregation) with wireless roaming, how should I set this up?"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by leo_m on 2012-06-21
How to configure the bonding to work with wireless roaming as well?

wpa_action is used to control roaming with list of networks defined in  the wpa_supplicant configuration file.  wlan0 interface is supposed to  be set to manual if one wants to use wpa_action, so that it (wpa_action)  can manage wlan0, but bonding also wants wlan0 to be set to manual so  it (bonding driver) can manage wlan0.  Two different programs trying to manage  the same interface wlan0 - will this cause any issues (like computer  hanging similar to what I witnessed when ifplugd and bonding were used simultaneously: see [http://ubuntuforums.org/showthread.php?t=1996289)?]("http://ubuntuforums.org/showthread.php?t=1996289%29?")  If  yes, then how to support roaming with bonding?

---

