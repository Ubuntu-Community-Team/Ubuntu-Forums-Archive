---
title: "Intel 810/Beryl no video overlay"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by LeSkip on 2006-11-11
A-hoy-hoy!

I successfully installed Beryl on my IBM X40 with Intel Extreme Graphics i810. Everything works perfectly, except for video overlay in VLC, Totem, Xine etc. 

I can see the image flickering briefly, but in general I get a black square.

What can I do to fix this?

Thanks in advance!

Skip

---

### Post by jackhynes on 2006-11-18
With VLC you do:

1. Go to Settings/Preferences/Video/Output modules/XVideo
2. Check the Advanced options below.
3. X11 display name change to 0, XVideo adaptor number to 0.

Thanks to kecsap

---

