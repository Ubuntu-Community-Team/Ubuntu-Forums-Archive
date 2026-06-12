---
title: "Slow graphics"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by alexanderkjerulf on 2006-08-13
I have Drapper on my LG laptop with only one major problem: Slow graphics.

Movies play fine in small size but are slow and choppy in full screen. Even the screen savers are r.e.a.l.l.y slow.

It's Intel 945GM and I've installed 915resolution, running in 1440x900.

Running xvinfo gives me this:
X-Video Extension version 2.2
screen #0
 no adaptors present

Any ideas will be greatly appreciated!

---

### Post by alexanderkjerulf on 2006-08-17
Got it!

in /etc/X11/xorg.conf I changed vesa to i810.

That's it :)

---

