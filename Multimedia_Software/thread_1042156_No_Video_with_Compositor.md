---
title: "No Video with Compositor"
date: 2009-01-17
forum: Multimedia Software
---

### Post by lastchancetosee on 2009-01-17
When using the xfwm-compositor strange stuff happens with videos:

mplayer only displays videos when in focus, otherwise displays a uniform blue background.
VLC, banshee and other players do the same, only with black backgrounds, in addition:
- sometimes VLC doesn't display anything even when in focus (fullscreen especially). Moving the window helps most of the time, but not always.
- when vlc, banshee, etc. are below another window, the video shows up partly in the top window. Redrawing (e.g. scrolling) of said window helps for a short while.

Switching of the compositor helps but really isn't a solution.

I've read somewhere that there are some problems with the compositor and ATI cards, but all the hints I got from there (disabling textured video, forcing EXA-acceleration) where ineffective.

Any ideas?

---

### Post by mistervinnie on 2009-01-22
I have the same problem. Used to work with Xubuntu 7.10, but on intrepid it seems to be a problem...

Normally i would not make a big deal about it and just shut it of, but i just got me the "avant-window-navigator" :D

---

### Post by lastchancetosee on 2009-01-28
When using Compiz under Xubuntu the problem persists. It even gets worse: Now MPlayer NEVER displays video, but only the blue screen. To think that I migrated from Windows to avoid blue screens ... :D .

But Compiz has some other problems as well, so I'm not quite sure whether or not this is the same problem.

---

