---
title: "mplayer won't play movie files with spaces or other special characters"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by ycason on 2007-11-27
When I try to play any files such as "blah blah.avi" or "foo[bar].mpg"  they won't play because of the space or brackets.  This doesn't happen when using totem.

Thanks

Edit: I've noticed that Mplayer is wanting to replace spaces with %20.  I completely removed mplayer and reinstalled, still no change.

---

### Post by mouldy on 2007-11-27
Weird, works fine with me. Tried renaming a few files to test it. Are you sure it's just the actual file that mplayer is having a problem with rather than the filename?


How are you trying to play them? From the gui or from a terminal/shell?

---

### Post by ycason on 2007-11-27
I've done both and on the terminal if I put the filename in quotes it works fine.  From Nautilus it never works.  Let me try to open one from within Mplayer.

Okay, if I browse to the file from within Mplayer it works.

---

### Post by ycason on 2007-12-06
Found the answer.  Edit the menu item for Mplayer to read "Mplayer %f"

---

