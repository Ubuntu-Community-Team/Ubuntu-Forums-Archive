---
title: "Fresh install of 11.10 - Unable to install restricted drivers for wireless"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by Gizim on 2011-10-14
HP 6450b
Broadcom STA Wireless Driver.
The wireless button is even off (amber) i can't turn it on.

Get "Sorry, installation of this driver failed"
Said to check jockey.log

2011-10-14 19:40:00,096 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:00,119 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:00,167 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:02,429 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:04,845 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-14 19:40:04,845 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-10-14 19:40:04,901 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:06,455 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:06,484 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:06,533 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-14 19:40:08,625 DEBUG: Shutting down

---

### Post by ericmitz on 2011-10-14
Having the same issue.

---

### Post by eombah on 2011-10-15
me too

---

### Post by steph7 on 2011-10-15
> **Gizim said:**
> HP 6450b
Broadcom STA Wireless Driver.
The wireless button is even off (amber) i can't turn it on.

please post
```
sudo rfkill list
```

---

### Post by Gizim on 2011-10-15
Got it fixed

Followed steps here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Had to uninstall bcmwl-kernel-source and reinstall the wireless switch doesnt work but i never turn it off any way.

---

