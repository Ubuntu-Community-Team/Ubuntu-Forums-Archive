---
title: "MythTV with fglrx with s-video output"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by Wwiillburr on 2007-08-14
With the generic ati driver in linux, my s-video output is not displaying correctly.
But when I use fglrx, it displays correctly on my monitor and my s-video out for TV

The problem is when I switch to fglrx, video playback in mythtv is choppy.

Is there some setting I should use or is that the nature of fglrx.
Because the generic ati drivers have no choppiness.

Thanks!

---

### Post by gator on 2008-07-11
yes video playback is choppy until i ran :-
sudo aticonfig --overlay-type=Xv

hope this helps

---

