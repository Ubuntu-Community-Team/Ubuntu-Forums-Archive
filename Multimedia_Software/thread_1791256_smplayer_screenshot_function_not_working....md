---
title: "smplayer screenshot function not working..."
date: 2011-06-26
forum: Multimedia Software
---

### Post by shantiq on 2011-06-26
... and was perfectly well until 3 days ago
now blanked out    it is allowed under options preferences

so there must be something to reset somewhere

any of you know?    thanx



ps on natty 64

---

### Post by papibe on 2011-06-26
Since smplayer is a gui to mplayer, you may try erasing mplayer's setting like this:
```
$ rm -rf .mplayer
```
Hope it helps.

---

### Post by SeijiSensei on 2011-06-26
Actually smplayer's configuration lives in ~/.config/smplayer.

What video card and driver are you using?  mplayer cannot take screenshots if you are using hardware acceleration with something like VDPAU.  Look in Options > Preferences > General > Video and check to see that you're using the "xv" video driver.

---

### Post by rvm4000 on 2011-11-07
The screenshot option is turned off if the folder for screenshots (preferences) does not exist.

---

