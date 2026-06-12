---
title: "Detect UVC driver is installed"
date: 2009-12-13
forum: Multimedia Software
---

### Post by narcisgarcia on 2009-12-13
(I've tried to ask this on [http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC) but some problem occurs editing that page)

In Bash, the only way I've found to detect if the driver is available on the system is this:
```

 sudo find /lib/modules | grep "/drivers/" | grep "/video/" | grep "/uvc"

```
Is there any other way to detect the driver, also without any webcam connected, and without depending of distribution/version?

---

