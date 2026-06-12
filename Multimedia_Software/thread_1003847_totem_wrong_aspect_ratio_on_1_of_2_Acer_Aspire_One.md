---
title: "totem wrong aspect ratio on 1 of 2 Acer Aspire Ones"
date: 2008-12-06
forum: Multimedia Software
---

### Post by binnian on 2008-12-06
I'm setting up 2 Acer Aspire Ones with 8.10.

Everything is working great so far except that 
on just 1 of them, 
totem displays videos horizontally squashed; 
on the other it's perfect.
(Behavior same in both firefox plugin and standalone player.)

I've meant to set these 2 identical machines exactly the same.
Totem settings seem to be identical (e.g. aspect ratio on Auto).

I tried deleting ~/.config/totem/state.ini
and all lines referring to totem in .gconfd/saved_settings
but to no avail.

I also tried complete removal and reinstallation of totem
on the bad one, again without fixing the problem.

I'm out of ideas, and baffled by why the 2 systems are
behaving differently. Any help greatly appreciated.

---

### Post by ChrisNiemy on 2008-12-28
Nearly the same issue here on a fresh intrepid install with all updtes (no backports, nor proposed updates). Two Desktop PCs running with 1024x768 resolution and the free Xorg "radeon" driver.

Maybe it's a xorg.conf issue. I read in other forums about this topic that one experienced when running ubuntu in so-called "low graphics mode" (which means, that a minimalistic auto-generated xorg.conf is used) aspect-ratio seems to be fine with totem again.

Maybe this happens when you configure your xorg.conf to explicitly, which happens quite often, when you're a "let's-tune-every-config-file"-nerd like me. ;-)

So just bumped this thread, and hopefully someone has an idea. For me the problem is that all clips, movies with an 4:3 ratio gets to 16:9. In window mode and in fullscreen.

---

### Post by ChrisNiemy on 2009-01-27
This is here is slighty related to our problem:
[http://dolphy-tech.net/log/?p=22](http://dolphy-tech.net/log/?p=22)
(check also the comments there!)

I will try if this can be fixed, with dpi settings in xorg.conf or some options like "PanelSize". Maybe it is useful to disable xinerama and xrandr completely.

---

