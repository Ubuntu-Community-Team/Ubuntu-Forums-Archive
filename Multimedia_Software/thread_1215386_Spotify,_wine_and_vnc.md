---
title: "Spotify, wine and vnc"
date: 2009-07-17
forum: Multimedia Software
---

### Post by masenius on 2009-07-17
We've had an old computer running win2k and spotify, connecting to it with tighVNC, to play some music in our testlab. Problem was it wasn't running that smooth, so I installed Xubuntu and spotify with wine. Works perfect when on that computer, however, when we connect to it over vnc, all the buttons in the spotify window has disappered. You can still interact with them, but they are invisible. Also there seems to be some default "move" command, which makes the window (or any songs) come in to move mode when clicking on them.

This is only for spotify, everything else works without a problem over vnc. Does anyone has any suggestions?

---

### Post by canadiandude007 on 2009-07-17
Do you have any screenshots of the problem?  I was able to use Spotify in Xubuntu without any issues, but did not test using VNC.  It could be the VNC configuration (screen config, mouse/keyboard commands) or a bug.

---

### Post by masenius on 2009-07-17
Here's a screenshot.

---

### Post by canadiandude007 on 2009-07-17
I would try launching Spotify from the command line to see any debug messages you come across.  Hard to tell what might be going on there.  Try ensuring VNC uses maximum screen depth settings.

---

