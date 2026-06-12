---
title: "recent erratic behavior of rhythmbox"
date: 2008-08-21
forum: Multimedia Software
---

### Post by SpaceMaster on 2008-08-21
Just in the last couple of days, Rhythmbox has been acting strangely.  What I find most strange is that in the period it broke, I didn't tweak it, change its library, install or remove any codecs (or is it codices?) or any kind, or even receive any updates!

I know this isn't much to go on, but here are the symptoms:
Upon startup, one of two things happens.

First scenerio, the rhythmbox window doesn't appear (despite "Show Music Player" being checked upon the previous close).  Clicking this box sometimes takes several attemps before the window actually appears.

The second scenerio is more troublesome.  If the GUI launches first attempt, then things go wrong.  hitting play freezes it for a short period of time (though none of the other buttons).  Use of any of the keyboard's media buttons, however, will cause the same effect.  Even the volume buttons do, which confuses me even more (since they don't directly control rhythmbox, but the ALSA mixer instead).  During these GUI freezes, music continues to play normally, but I can't control it until the program unfreezes.  Minimizing the window, or moving it to an inactive workspace seem to abate the issue (but then there's the problem of not being able to change to whichever song to which I listen).

So does anyone have any suggestions?  And no, I have not yet tried 
```
$ sudo apt-get remove --purge
```, but if I can reasonably avoid that, it would be nice.

---

