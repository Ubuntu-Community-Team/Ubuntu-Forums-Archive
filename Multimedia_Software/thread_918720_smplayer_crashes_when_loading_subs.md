---
title: "smplayer crashes when loading subs"
date: 2008-09-13
forum: Multimedia Software
---

### Post by alejaaandro on 2008-09-13
hey guys, need some help plz... smplayer crashes sometimes when i try to load an .srt file... by sometimes i mean it does it only with some movies, even if i try a different .srt file...

the strange thing it doesn't completely crash: to screen closes but the audio keeps playing and i have to kill the process to stop it....

any ideas why that happens? 
if you need any more info, just tell me...

---

### Post by rvm4000 on 2008-09-13
What version are you using?

Could you try the latest one?

[ftp://ftp.berlios.de/pub/smplayer/](ftp://ftp.berlios.de/pub/smplayer/)

---

### Post by Uhuu on 2008-09-16
have the same problem, and latest version didn't fix it for me.

---

### Post by rvm4000 on 2008-09-16
I can't reproduce those crashes when loading subtitles.

Anyway I added in svn r1802 a check in the function which selects the subtitles to avoid to use an invalid index. That should prevent crashes.

Have you tried that version?

It it still crashes then the problem should be in another place...

---

