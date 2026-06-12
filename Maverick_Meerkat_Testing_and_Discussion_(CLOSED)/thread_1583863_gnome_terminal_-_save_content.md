---
title: "gnome terminal - save content"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2010-09-28
If you blinked you wouldn't have noticed this. I don't usually cross-post, but it seems important to bring this up in the Maverick forum. See this beginners forum thread:

[http://ubuntuforums.org/showthread.php?t=1581762](http://ubuntuforums.org/showthread.php?t=1581762)

In short, the 'save content' option in the File menu of the gnome-terminal was there in Lucid but has disappeared in a recent update. Now the same has happened in Maverick with gnome-terminal going from 2.31.91 to 2.32.0. If you did blink - as I did at first - you wouldn't have found a nifty little utility. It saved the output from the last terminal command to a text file.

Anyone know where errant terminal utilities go when they're on walkabout and if we might ever see them again?

Ho-hum. They give with the left hand and then take away with the right.

---

### Post by mc4man on 2010-09-28
from the .32 source
> /*
* We don't want to enable content saving until vte supports it async.
* So we disable this code for stable versions.

---

### Post by coffeecat on 2010-09-28
Thanks. It must have been a hiccup for it to have got (temporarily) in the release version of Lucid. It was an install from the 10.04.1 ISO that I saw it in briefly.

What's vte in the "until vte supports it async" bit?

---

### Post by Dayofswords on 2010-09-28
> Definition: vte: VTE is an experimental terminal emulator widget for use with GTK+ 2.0. 

[http://linux.about.com/cs/linux101/g/vte.htm](http://linux.about.com/cs/linux101/g/vte.htm)

---

### Post by coffeecat on 2010-09-28
Thanks. 

> **Dayofswords said:**
> [http://linux.about.com/cs/linux101/g/vte.htm](http://linux.about.com/cs/linux101/g/vte.htm)

And...

> Source: Mandrake 9.0 RPMLooks as though they've been experimenting long enough. :(

:wink:

---

