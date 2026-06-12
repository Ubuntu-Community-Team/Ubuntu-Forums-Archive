---
title: "wireless card hard blocked"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Wessel on 2012-12-17
Hi,

I recently installed ubuntu 12.10 on my medion erazer laptop. The wireless card seems not to be working properly. The command "rfkill list" shows it is hardblocked.

On my windows installation it's possible to use my FN-buttons to activate my wireless. On ubuntu this is not possible.

What could be the problem?

---

### Post by kurt18947 on 2012-12-17
I'm not certain.  One thing you can check though.  When you exit Windows, do you leave the wifi adapter enabled?  There used to be an issue where if a wireless adapter were disabled in Windows, it could not be enabled in Ubuntu.  It's also possible that Ubuntu doesn't recognize/support your machine's F key combination switches.  

You could also try this in a terminal from an account with sudo privileges:

```
sudo rfkill unblock all
```

---

### Post by Wessel on 2012-12-17
I've already tried that but it won't make any difference

---

### Post by Buntu Bunny on 2012-12-18
I had to disable bluetooth before I could get the Fn key to work and turn on my wireless.

---

