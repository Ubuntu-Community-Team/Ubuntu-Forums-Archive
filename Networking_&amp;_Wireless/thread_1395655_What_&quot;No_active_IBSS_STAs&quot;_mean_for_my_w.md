---
title: "What &quot;No active IBSS STAs&quot; mean for my wireless?"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Turin Turambar on 2010-02-01
Every time I run DMESG command, I get 

```
[ 6088.931258] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6088.991261] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.051256] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.111259] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.171257] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.231257] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.291258] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.351257] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6089.411256] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

```

My wireless network is working normally in ad-hoc mode. I have normal file sharing & internet on the other computer.
Is there a way to stop scanning for IBSS (whatever that means...)?

---

### Post by Turin Turambar on 2010-02-01
Apparently that was a bug in ath5k driver and is fixed in Kernel 32.7 release, which I'm using now.

---

