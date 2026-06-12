---
title: "wireless connection upon boot"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by 696f6e6963 on 2009-07-08
I have a bunch of Dell Mini's which I was able to get to authenticate with AD. The problem is, they will only authenticate when they are wired. I have a feeling it is because the wireless does not connect until you log on, and when you log off, it disconnects. Which is a problem. No wireless connection - no authentication. How can I make wireless connect during boot up before the user logs in so they can authenticate wirelessly?

Thanks,
John

---

### Post by 696f6e6963 on 2009-07-13
Anyone?

---

### Post by bernied on 2009-07-13
I use wicd instead of network-manager to manage wireless. Once you setup your preferred wireless networks, they will connect at boot.

You could also configure wpa_supplicant directly.

---

