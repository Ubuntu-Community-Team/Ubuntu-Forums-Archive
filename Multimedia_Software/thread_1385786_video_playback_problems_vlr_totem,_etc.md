---
title: "video playback problems vlr totem, etc"
date: 2010-01-20
forum: Multimedia Software
---

### Post by ryan83189 on 2010-01-20
Previously my ubuntu machine played videos perfectly fine. now opening those videos with vlc results in a blue or black screen with audio, or the program starts and closes immediately. This is what happens with the default media player as well. These files were played on ubuntu before, and work in windows with vlc just fine. 
Here is a printout of what happens when I run it

```

rmahoney@netbook:~/Desktop$ vlc movie.avi 
VLC media player 1.0.2 Goldeneye
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3c00005


```

the last 4 lines are printed over and over again, but for scrolling sake I ommited them. I first noticed it yesterday, I update my system whenever prompted to, and think the last time that it worked a about week ago.

---

### Post by mc4man on 2010-01-20
Did you happen to install cairo-dock?

---

### Post by ryan83189 on 2010-01-20
nope, nothing has changed except normal updating. I should also mention I have 9.04 netbook remix if that makes any difference.

---

