---
title: "Nvidia TNT2 card and Xubuntu"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by JKyleOKC on 2008-01-05
I'm running Xubuntu on an ancient Gateway box that has a TNT2 video card driving a flat panel display, and have a strange problem if I use the "nv" driver even after installing the legacy version that is supposed to work with the older cards. The display is offset vertically!

That is, there's a horizontal line about the middle of the screen. The top half of the display is below this line, while the bottom half is above it.

Everything still works, but it's quite strange to move the mouse pointer off the bottom of the screen and have it reappear at the top.

Editing xorg.conf and changing the driver to "vesa" makes it all work normally, but my GL screensavers don't work. I'm fond of the GLText (clock) saver so would like to get everything working properly with the customized driver rather than with vesa.

The "related" threads don't seem to address this specific problem. Has anyone else run into it? From my dabblings in analog TV and working with the designers of some of the very first video terminals back in 1965, I suspect that it has something to do with a mis-timed vertical sync signal -- but have no idea how to fix it.

---

