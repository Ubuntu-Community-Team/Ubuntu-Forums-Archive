---
title: "Rhythmbox quits when playing midi files with crossfading"
date: 2008-12-21
forum: Multimedia Software
---

### Post by phenest on 2008-12-21
Just a quick post in case anyone else is having this problem. I found that when clicking 'Next' to play the next midi track, Rhythmbox quits with a seg fault. This only happens with crossfading on. I reported this on Bugzilla [564930]("http://bugzilla.gnome.org/show_bug.cgi?id=564930") which turned out to be a bug in the wildmidi library which has also been reported on [SourceForge]("http://sourceforge.net/tracker/index.php?func=detail&aid=2454029&group_id=42635&atid=433744").

---

