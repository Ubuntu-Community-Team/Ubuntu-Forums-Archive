---
title: "Rhythmbox always monitoring ~/Music"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Steeperton on 2010-05-06
Rhythmbox keeps re-importing items in ~/Music, even though I've changed the library to something else (/media/tunes if it makes a difference). 

I've changed this in both Rhythmbox and checked gconf-editor, and neither shows this directory as being monitored...

How do I stop this?

---

### Post by doas777 on 2010-05-06
one of the things I would check, are the permissions and ownership on /media/tunes.
it sounds like it may be falling back to a default location because the new one can't be used.

---

### Post by Steeperton on 2010-05-11
Unfortunately I've tried that, and permissions are set fine.

Also noticed today that it's not just ~/Music that's being monitored... It's my entire Home directory - had some MP3s in "Downloads" and these got added too!

---

