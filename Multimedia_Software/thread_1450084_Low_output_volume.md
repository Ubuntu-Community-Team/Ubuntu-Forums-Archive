---
title: "Low output volume"
date: 2010-04-08
forum: Multimedia Software
---

### Post by JClaxton on 2010-04-08
I have a dual boot system with XP and Ubuntu 9.04. When I boot into XP the volume is fine, but when I boot into Ubuntu the output volume is half what it is in XP. I have to crank my stereo way up to get it to a decent volume. 
Is there any way to boost the output volume in Ubuntu?

---

### Post by lidex on 2010-04-08
Try "System>Preferences>Sound"
And in a terminal="Applications>Accessories>Terminal":
```
alsamixer
```
Press F3 for playback levels. Scroll right with right-arrow key to "Line". Use up/down keys to adjust level. Alternately, adjust PCM/Front.

---

### Post by JClaxton on 2010-04-09
That's what I was looking for.  Thanks!

---

