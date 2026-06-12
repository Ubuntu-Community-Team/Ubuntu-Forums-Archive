---
title: "Totem / Xine broke today, no clue why"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by Laemel on 2007-05-02
So, I'm running Feisty, and everything's been working fine.  Everything was working fine last night, I was watching videos with Totem.  I didn't log out or shut my computer down, and the next morning Totem crashed when I started it.   If I go to a command line and start totem I get:

```
Segmentation fault (core dumped)
```

I tried starting xine directly, and it's the same thing:  It starts and it's window pops up, then immediatly crashes:

```

This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
Segmentation fault (core dumped)

```

I didn't install anything or restart, I seriously didn't even touch my computer.  It worked, I went to bed, got up, now it doesn't work.  I tried making a new user account and it works fine when I'm logged in with that, but not in my own account.  I've tried clearing out all the Totem configuration stuff from ~/.gconf and ~/.gnome2, but that doesn't help.... Any ideas?

---

### Post by theantix on 2007-05-13
Same thing happened to me.  I fixed it by renaming the ~/.xine/ directory, works fine now.

---

