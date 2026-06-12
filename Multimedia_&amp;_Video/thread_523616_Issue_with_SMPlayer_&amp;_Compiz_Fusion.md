---
title: "Issue with SMPlayer &amp; Compiz Fusion"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by GFree678 on 2007-08-12
I've got an issue with the fullscreen mode of SMPlayer when running Compiz Fusion. If I press 'F' to enter fullscreen mode and press it again to return to windowed mode, the player window shifts down by a small bit, about the height of the window title bar. This means that if I keep flicking back between fullscreen and windowed modes, the player window on the desktop will eventually move down far enough I have to pull it back to the right spot.

It keeps its place properly when using Metacity, so I'm guessing Fusion's window placement rules are interfering. Anyone have any suggestions on how to keep things from moving?

---

### Post by Gremlinzzz on 2007-08-12
Did you configure smplayer if not make the video X11.

---

### Post by GFree678 on 2007-08-12
The video output was already set to X11, but thanks anyway.

---

### Post by rvm4000 on 2007-08-12
(I'm the developer of smplayer)

I'll try to find a fix for this problem for the next release.

---

### Post by GFree678 on 2007-08-12
I've just checked, and I notice the same issue occuring with some other programs. Like Synaptic, I open the program, close and reopen, and the window has shifted down a bit just like with SMPlayer.

Definately seems to be related to Fusion's window placement settings, buggered if I know what though. SMPlayer itself is probably just fine though, I wouldn't worry much since you'll give yourself a headache finding a bug that isn't there. :)

---

### Post by rvm4000 on 2007-08-12
Too late, I already added an option to try to fix that problem.

In fact that problem was present in Windows (but in this case the window moved up) so there was already code for this, but it was only used under Windows.

Now I made it a configurable option (for now only available in the config file).
So if you want to test...

1) Download and compile the latest release: [smplayer-0.5.29-qt4-0813.tar.bz2](http://smplayer.sourceforge.net/porting/smplayer-0.5.29-qt4-0813.tar.bz2)
2) Run it once and close it (so it saves the new option in the config file)
3) Edit ~/.smplayer/smplayer.ini and look for the option **restore_pos_after_fullscreen** and set its value to true.
4) Save the file, run smplayer and see if it there's any difference.

---

