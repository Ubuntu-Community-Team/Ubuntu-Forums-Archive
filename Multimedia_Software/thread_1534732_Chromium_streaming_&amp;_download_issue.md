---
title: "Chromium streaming &amp; download issue"
date: 2010-07-20
forum: Multimedia Software
---

### Post by maddbaron on 2010-07-20
Hello,

 Recently whenever I try to watch streaming media in Chromium it stops after a few minutes. When I open the same stream in firefox/opera I don't get the issue. When I attempt to download something it stops at 40mb's in chromium but with other browsers I experience no problem. It just started about a week a go. 

Is there a way I can check the cache limits in Chromium? Or check something else to see what the problem is?

---

### Post by lovinglinux on 2010-07-20
> **maddbaron said:**
> Is there a way I can check the cache limits in Chromium? Or check something else to see what the problem is?

Chrome doesn't offer an **about[noparse]:[/noparse]config** page like Firefox, but you can add a switch to your launcher command like this:

```
google-chrome --disk-cache-dir="CACHE_DIR" --disk-cache-size=N
```

See more info [here](http://www.google.com/support/forum/p/Chrome/thread?tid=098d42a41aacdc6d&hl=en).

---

