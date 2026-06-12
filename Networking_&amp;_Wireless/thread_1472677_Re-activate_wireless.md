---
title: "Re-activate wireless"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by flyver on 2010-05-04
My Ubuntu 10.04 usually doesn't "see" any networks after waking up from a "suspend". However, after a _reboot_ it always sees them and connects to them without any problem. Is there a terminal command or anything like that I could do manually to make it seach for networks?

Thank you!

---

### Post by meithan on 2010-05-04
> **flyver said:**
> Is there a terminal command or anything like that I could do manually to make it seach for networks?

Yes:

```
iwlist wlan0 scan
```

where 'wlan0' is the name of your wifi network interface; to find out what it is in your computer, do

```
iwconfig
```

and you'll see your network interfaces - the one stating some info instead of 'no wireless extensions' is your wifi network interface name.

Edit: however, I'm thinking that if the systray icon (Network Manager) can't see any networks, then it's probable that iwlist won't either. Let us know.

---

### Post by flyver on 2010-05-04
Thank you, however that doesn't seem to fix my problem after all. I really thought it would...

"Failed to read scan data : Network is down".

Hmm.

---

### Post by flyver on 2011-01-12
I definately hate Intel® PRO/Wireless 3945ABG. I've had this annoying problem for a year now... :(

---

