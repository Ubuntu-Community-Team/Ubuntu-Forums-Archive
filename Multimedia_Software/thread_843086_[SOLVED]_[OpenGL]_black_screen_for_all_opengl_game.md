---
title: "[SOLVED] [OpenGL] black screen for all opengl games"
date: 2008-06-27
forum: Multimedia Software
---

### Post by kakyoism on 2008-06-27
I just installed Neverball, Nexuiz, and a few other opengl related games.
But all I got is black screen. In some cases, I couldn't even turn on a new terminal with ctrl+alt+F1....

Meanwhile I can play Pingus perfectly.
Does it have everything to do with my OpenGL?
Please help!
Thanks.

---

### Post by dandawong on 2008-06-27
Have you turn on compiz?
System --> Appearance --> Visual Effects, set it to None and retry the opengl games.

---

### Post by kakyoism on 2008-06-27
compiz was off when the problem happened.

There is one more thing: I was running dual-head, with 
different resolutions, 1. my laptop on 1280x800, 2. an LCD on 1280x1024.
when I played Gridwar, 
both screen showed the same game main screen , but when entered the game, 
the screen was dead, and I was brought into a warning dialog of 640x480 resolution, and forced to test the screen, looks like X-server kinda thing.

---

### Post by kakyoism on 2008-06-28
I solved it myself: it was due to my dual-head.
Once I switch to single-head, they all become playable.

---

