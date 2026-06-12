---
title: "MP3s skipping"
date: 2009-10-30
forum: Multimedia Software
---

### Post by Phil-Reeve on 2009-10-30
MP3s tend to skip on my Xubuntu installation (they did on Ubuntu as well which is why I thought I'd try Xubuntu).  I've tried mpg123 (with playmp3list front end) as it's supposed to be a really efficient MP3 decoder, but I still get the problem.

It's a fairly old 1GHz Pentium III laptop but I would have thought that it could play MP3s alright.

Has anyone got any ideas for anything I could try?  My user level's something like intermediate, although I can always usually dig deeper in to Linux and get there in the end.

Thanks

Phil

---

### Post by Shpongle on 2009-10-30
did you install xubuntu-restricted-extras 

sudo apt-get install xubuntu-restricted extras ?

---

### Post by Phil-Reeve on 2009-10-30
No, what would that do?

---

### Post by w0rds on 2009-10-31
I'm having this problem on Ubuntu 9.10 also.
Tried playing through different players (Banshee and Songbird); killing pulseaudio didn't work either.
Very annoying problem...

---

### Post by w0rds on 2009-10-31
BTW:

Tried to install ubuntu-restricted-extra and nothing changed. The problem is not decoding MP3s I guess. The player plays the music, but skips a few parts (or sometimes the whole song).
Plus, the same happens with OGG.

---

### Post by Phil-Reeve on 2009-10-31
I installed xubuntu-restricted-extras and then Amarok and it seems a lot better now.  I think giving Amarok a higher priority in System Monitor helps as well.  Also set up MySql for Amarok's DB, but it seems the same to me as before...

Strange, and annoying... I could probably put Windows on it and be OK.

---

