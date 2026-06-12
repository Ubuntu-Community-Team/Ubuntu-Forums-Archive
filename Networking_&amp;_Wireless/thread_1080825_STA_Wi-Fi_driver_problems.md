---
title: "STA Wi-Fi driver problems"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by BiynaYahu on 2009-02-25
I am running a Dell Inspiron 1501, and just attempted to switch over to the new proprietary Broadcom STA driver.  I followed the advice in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) , but when I booted back up while it would tell me that I was connected to my router (wirelessly), I could not use the internet (bring up pages) wirelessly or wired.  Any help would be great.  Thank you in advance.

P.S. Also the B43 driver is no longer in Hardware Drivers.

---

### Post by BiynaYahu on 2009-02-25
Alright.  So, when I activated the STA driver it automatically blacklisted the B43 driver.  Therefore, I deactivated STA, and re-activated B43 allowing me to use the internet once again.  Although, I still cannot access the internet while wired to the router.  So, if anyone has any pointers on that that would be great, but I'm just switching back to B43.

---

### Post by wirelessben on 2010-01-01
You're not alone. The STA driver install just hangs, and I can't cancel.

I'm on 9.10 64-bit.

---

