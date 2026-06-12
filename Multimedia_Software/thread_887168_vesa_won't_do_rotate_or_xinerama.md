---
title: "vesa won't do rotate or xinerama"
date: 2008-08-11
forum: Multimedia Software
---

### Post by scheutz2002 on 2008-08-11
I have a new Radeon HD 4850 video card.  The vesa driver refuses to take
my 'Option "Rotate" "left"', etc, that worked on an old Matrix MGA G400.
The log always has a message: 'Option "Rotate" is not used'.  I have 
tried the Rotate option in the Device sections (where it is on the old 
setup), and also in the Monitor and Screen sections, with the same result. 

Slightly differently, it claims in the log to enable Xinerama, but doesn't
actually do it.  I just get cloned monitors.

(Aside: all attempts to use more specific drivers (radeon, radeonhd, fglrx) 
fail to recognize the 4850, but that's a separate problem.)

---

