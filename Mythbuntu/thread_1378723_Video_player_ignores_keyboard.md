---
title: "Video player ignores keyboard"
date: 2010-01-11
forum: Mythbuntu
---

### Post by movieman on 2010-01-11
So does anyone know why the MythTV internal video player now ignores my keyboard? The only thing I can do if I start playing a video file is either wait for it to finish or CTRL+ALT+BACKSPACE to kill X11.

I knew I shouldn't have upgraded to 0.22...

---

### Post by movieman on 2010-01-11
So, playing back recordings works fine. Playing back video files does not: keyboard doesn't work, mouse buttons don't work, the only thing it recognises is the mouse wheel. The keyboard is clearly working because ALT+TAB and CTRL+ALT+BACKSPACE work.

Actually accepting commands from the user seems like a fairly basic and significant thing to not work.

---

### Post by movieman on 2010-01-12
Ok, looks like this is likely to be the problem:

[http://svn.mythtv.org/trac/ticket/7366](http://svn.mythtv.org/trac/ticket/7366)

Guess I'd better find a way to disable bookmarks in the playback.

---

