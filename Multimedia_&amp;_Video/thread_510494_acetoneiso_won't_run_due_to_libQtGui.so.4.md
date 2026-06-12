---
title: "acetoneiso won't run due to: libQtGui.so.4"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by spacepirates on 2007-07-26
I've been trying to mount an iso image for about a week now, and Acetoneiso seems like the solution to my problems except that i keep getting this error:
```

spacepirates@spacepirates-desktop:~$ acetoneiso2
acetoneiso2: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory

```

and so i am left with nothing. i've tried fuseiso, gmountiso, and even the regular mount command and none of them will work.

right now i am on Kubuntu feisty, but can switch over to Ubuntu if need be.

help? thanks!

---

### Post by justin whitaker on 2007-07-26
Try this:

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

That script  looks like a keeper for situations like these.

---

### Post by spacepirates on 2007-07-26
works fantastically after installing libQtGui.so.4 with getlibs.


thanks for the quick help!

---

