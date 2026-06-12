---
title: "fglrx question"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by 25an on 2006-10-17
Hi!

I have installed fglrx driver for my ati card and it works fine so far. But i have one question when i run fglrxinfo i get following:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

It looks fine except for one thing my card is a RADEON 9600 Pro,
is this something to fix or not?
If i change it in /etc/X11/xorg.conf is that ok?

I don't now if it has anything to do with it but i could not get 
aticonfig --initial to work so I had to manually edit /etc/X11/xorg.conf from "ati" ro "fglrx"

Thanks.

---

