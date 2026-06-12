---
title: "[SOLVED] amarok no window manager"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by kooldino on 2008-01-06
For some reason, my amarok player in KDE runs in full screen mode with no window manager (even though the rest of my programs have one).

I run compiz, but even when I run kwin as the window manager, it still refuses to use one.  I did a reinstall of the program through the package manager, but it didn't help.

Is there a way to start it via command line or something to force it to have a window manager?  What gives?

---

### Post by kooldino on 2008-01-09
bueller?

---

### Post by kooldino on 2008-01-13
Can anyone suggest a solution for me?

---

### Post by ignignokt00 on 2008-01-16
I had the same thing with Totem in Gnome, using Compiz Fusion.  I dunno if it's related.

Try starting Amarok, then hit alt+F2 and run "kwin --replace", then see if you can restore that window to its normal size.  Then run "compiz --replace".

Or maybe you just have Amarok in fullscreen mode?  Try hitting F11 in Amarok.

---

### Post by kooldino on 2008-01-27
ALT+F2 doesn't do anything.

F11 does nothing as well.

---

### Post by kooldino on 2008-02-11
bump

:guitar:

---

### Post by kooldino on 2008-02-11
Solved it by fixing something else (read post #9)

[http://ubuntuforums.org/showthread.php?p=4313621#post4313621](http://ubuntuforums.org/showthread.php?p=4313621#post4313621)

In a nutshell, I think it was some kind of window manager conflict during KDE startup.

---

