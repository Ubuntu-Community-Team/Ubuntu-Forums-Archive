---
title: "Animated wallpaper dual monitors"
date: 2009-05-01
forum: Multimedia Software
---

### Post by zigga15 on 2009-05-01
Hey all,

I am having a bit of fun with the pretty things in linux. I have followed these posts to get an animated desktop going

[http://blog.prashanthellina.com/2007/08/22/matrix-desktop/](http://blog.prashanthellina.com/2007/08/22/matrix-desktop/)
[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

The problem is, I can only get the animated desktop on my primary monitor, my secondary one doesn't do it.

This is the command I use to start it up is like this:

```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID

```

Has anyone managed to get this working on both monitors, I can't figure it out... it seems that the -fs option makes it full screen but for the primary monitor.

Any help would be great!

~ Dan

---

