---
title: "Desktop Cube/wobbly windows issue."
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LordDelta on 2011-04-18
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/436343](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/436343)

...I'm not sure if this is related, and now that I'm trying to report the problem, I'm having problems reproducing the conditions/taking the screenshot, but I'm having an issue where other windows that are not being directly manipulated are...bending, when I move other windows (i.e. if I have gedit open and fullscreen and move a terminal around over it, the gedit instance warps around as I move the terminal instance). I have the compiz wobbly plugin enabled as well, as does the bug reporter, and the cube desktop plugin (and the rotate cube) plugin enable instead of the wall plugin.

Basically if anyone knows if there is a way to get rid of this 4 desktop fused setup, and revert to the old cube desktop, that would solve half of my problem.

The other half would be to resolve the odd functionality with the wobbly windows, if this is possible.

---

### Post by mc4man on 2011-04-18
>  this 4 desktop fused setup
While I'm not sure what you mean if it's that you have a 2x2 instead of a 1x4 desktop size then open ccsm > General Options > Desktop Size and adjust.
Never used a wobbly window except to disable

---

### Post by LordDelta on 2011-04-18
Woo. That part works!

If I may say so, it wasn't obvious (to me) to look in the general options, for something I was trying to fix in the cube. Also that I'd have to set the horizontal virtual desktops to 4, instead of the regular desktops. Which, is, not exactly what I wanted (I wanted 4 separate desktops on the cube, not a cube of a virtual desktop that's 4 desktops wide). Should I report a bug, or is there another setting I've overlooked somewhere?

I.e. this shouldn't happen:

[[IMG]http://img820.imageshack.us/img820/6271/screenshotnd.th.png[/IMG]](http://img820.imageshack.us/i/screenshotnd.png/)

(notice how the browser is in the middle of two desktops)

---

