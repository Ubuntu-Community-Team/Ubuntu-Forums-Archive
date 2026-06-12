---
title: "Can't set channel on Intel WLAN 2100 3B Mini PCI"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by EmperorMoo on 2009-01-05
I've had a look around for the fix to this issue and can't see anything.

I upgraded an elderly laptop to 8.10 from Hardy, and now I can't set the wireless channel.  I can see my network and those of my neighbours with iwlist scan.

When I try to set the channel (using sudo iwconfig eth1 channel xx) I get the following message:
```

Error for wireless request "Set frequency" (8B04):
SET failed on device eth1 ; operation not supported

```

All other settings (essid, ap, key) can be set no problem.

---

