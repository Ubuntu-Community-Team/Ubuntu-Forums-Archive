---
title: "flashing video"
date: 2008-09-14
forum: Multimedia Software
---

### Post by mrblue182 on 2008-09-14
When I watch a video on miro, VLC, or totem, the video is flashing either black or white depending on the player. Either that or the player immediately crashes as soon as I try to play the video. I can get videos to work if I use this command

```
mplayer -vo x11 -autosync 1000 [filename]
```

but that is terribly inconvenient, and the video is about 1/4 the size it should be.

---

### Post by skullmunky on 2008-09-16
in the player preferences, look for a place where you can choose different video drivers.  if it's Xv, try something else, like X11, or OpenGL, etc.  

oh wait that's what you're doing already with the -vo flag, isn't it...

---

### Post by mrblue182 on 2008-09-16
I found that command in anther thread with this same problem, but it's not a very good experience. The video is really small, and I have looked around the options in all the players and have yet to find any thing like you're talking about. Thanks in advance for the help!

---

### Post by mrblue182 on 2008-09-17
Never mind, I found out where to change the video =]

for those who find this thread with the same problem, for VLC you go

Settings > Preferences > Video > Output Modules (check advanced options at the bottom right) > and you choose the video output X11.

---

