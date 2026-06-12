---
title: "No Wireless Driver Upon Updating"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by bruce247 on 2013-02-27
Every time I update Ubuntu 12.04 I have to reinstall my wireless driver for wifi to work. Does someone know an easy way I can fix this?[COLOR=#000000][/COLOR]

---

### Post by kurt18947 on 2013-02-28
If the image/kernel is upgraded, it's normal to have to rebuild.  DKMS takes care of this but is not universal.  There is a way to automatically *load, *but not rebuild/reinstall without DKMS.  At least that's my understanding.

---

