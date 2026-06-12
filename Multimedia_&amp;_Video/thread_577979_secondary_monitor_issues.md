---
title: "secondary monitor issues"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by ToastBusters on 2007-10-16
Hey everyone,

I have two screens hooked up to an nvidia 8800GTS card. I enabled the restricted driver without any issues, but when I opened the "screens and graphics" window to enable the secondary monitor, the option is grayed out. It only seems to recognize the first screen.

I'm not sure what I could post in here to help resolve this issue, but any help would be great.

---

### Post by NT4usB on 2007-10-16
from a terminal:```
sudo nvidia-settings
``` will give you root access to the ap.
I'm not sure you can set it up that way though... I've only done it manually by editing xorg.conf.
There's a bazillion threads on dual monitors on these boards. Have a quick search and see what you find...

---

