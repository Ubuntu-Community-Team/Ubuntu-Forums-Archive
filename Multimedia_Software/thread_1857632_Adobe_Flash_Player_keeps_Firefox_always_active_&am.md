---
title: "Adobe Flash Player keeps Firefox always active &amp; running"
date: 2011-10-10
forum: Multimedia Software
---

### Post by mamboknave on 2011-10-10
Symptoms:
When restarting FireFox, this msg appears and FireFox does NOT restart: "FireFox is already running but is not responding"

Causes:
It happens if and only if, initially, FireFox used the FlashPlayer. It is the FlashPlayer process that keeps the FireFox process hanging and active even after the FireFox window get closed.
In fact, after closing the window, I see both processes (FireFox & FlashPlayer) still active.

If FireFox does not open the FlashPlayer, everything goes fine (the symptom does not occur).

QUESTION: Is there any known way to fix this problem?

P.S. My system setup: Ubuntu 10.04 32b, FireFox 3.6.23 FlasPlayer 11.0.1.152-0lucid1

---

### Post by lovinglinux on 2011-10-10
The easiest workaround would be to kill firefox-bin.

```
killall firefox-bin
```

However, this isn't a solution. I would recommend trying Firefox 7. See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247).

---

