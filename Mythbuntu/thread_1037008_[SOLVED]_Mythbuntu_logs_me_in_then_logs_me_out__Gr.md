---
title: "[SOLVED] Mythbuntu logs me in then logs me out | Graphics problem? Help please..."
date: 2009-01-11
forum: Mythbuntu
---

### Post by RonPDX on 2009-01-11
Good morning everyone, 

Last night I had to switch over to XP to use iTunes, this morning I tried to log back into Mythbuntu but for some reason I get kicked right back out to the login screen. Sometimes my monitor will roll horizontally forcing me to do a hard restart, this makes me think there is a graphics problem. I have tried to login using the different session options and the only one that works is the terminal, but since I don't know where this problem is I don't know where to start as far as command line is concerned. 

Any Ideas?

Ron

*Update*

Found that the problem was my Window Manager was crashing, if anyone is having the same problem there was a solution from another thread that suggested moving my config file using the code below

```
mv ~/.config ~/.config.old
```

---

