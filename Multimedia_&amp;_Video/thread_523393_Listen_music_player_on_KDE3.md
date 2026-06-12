---
title: "Listen music player on KDE3"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by rpkehoe on 2007-08-11
I recently saw the Listen media player on a friends Ubuntu machine and thought I should check it out.  But I have not been able to get it to actually play anything on KDE 3 at all.  Everything else works fine, but when you press play, it just sits there.  If you try dragging out the the tracking bar, it just goes back to the beginning.

The odd thing is that this only happens under KDE 3.  I have tried it under Gnome, fluxbox, xfce, and even KDE 4, and they all work.

Anyone else run into this?  This is just a straight install from the repos, I might try compiling it next.

---

### Post by rpkehoe on 2007-08-11
Compiling certainly did not help.  I don't know enough about python to make a sense of this:

$ listen
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 66, in <module>
    import utils, const, stock, config
  File "/usr/lib/listen/utils.py", line 33, in <module>
    import stock
  File "/usr/lib/listen/stock.py", line 78, in <module>
    import const
  File "/usr/lib/listen/const.py", line 116
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

---

