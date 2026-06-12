---
title: "[SOLVED] smplayer transport controls greyed out"
date: 2008-12-21
forum: Multimedia Software
---

### Post by davidself1001 on 2008-12-21
I have installed/removed/installed smplayer a number of times and so far every time all of the transport controls (ie play, stop, rewind, etc) are greyed out both on the player gui as well as in the drop down menus.  Any ideas what could be causing this?  I can play a video but i have no control over it (not even with keyboard shortcuts).

---

### Post by rvm4000 on 2008-12-22
That happens when smplayer can't read the output from mplayer.

Maybe you have an option in your ~/.mplayer/config that disables the output, like -really-quiet.

---

### Post by davidself1001 on 2008-12-22
> **rvm4000 said:**
> That happens when smplayer can't read the output from mplayer.

Maybe you have an option in your ~/.mplayer/config that disables the output, like -really-quiet.
That was it.  thanks!

---

