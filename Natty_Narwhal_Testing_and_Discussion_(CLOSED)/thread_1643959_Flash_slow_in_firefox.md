---
title: "Flash slow in firefox"
date: 2010-12-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-12-12
Flash works fine in Opera and Chromium but is rather choppy in Firefox. I tried with and without Compiz, with Nouveau and the Nvidia BLOB - no change. 

I also tried to run this "put OverrideGPUValidation=true in a file called /etc/adobe/mms.cfg"-thing - no change.

Anyone else seeing this? Any ideas?

---

### Post by cariboo on 2010-12-12
Flash crashes on me when using chromium, so I open firefox to view anything needing flash, I haven't noticed any performance problems, except for buffering when viewing 1080p videos, and that doesn't happen all the time.

---

### Post by drdos2006 on 2010-12-12
You may be having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.

regards

---

### Post by MacUntu on 2010-12-12
So it's just me? Stupid thing! :-/

> **drdos2006 said:**
> You may be having IPv6 problems in your browser.

Thanks, but isn't that just a DNS related problem? Anyways, it didn't change flash performance. :(

---

### Post by MacUntu on 2010-12-13
Do I need this 'flashplayer-nonfree' package installed?

about:****plugins shows

```

Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r32
```

---

