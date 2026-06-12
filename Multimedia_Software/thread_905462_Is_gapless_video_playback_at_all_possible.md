---
title: "Is gapless video playback at all possible?"
date: 2008-08-30
forum: Multimedia Software
---

### Post by frankvw on 2008-08-30
Any guru's out there? I sure hope so, because this is driving me crazy.

For a digital signage application I need gapless video playback. I've gone through Mplayer, Totem, VLC and what not, and they all insert a big ugly gap between video clips (either showing the desktop or the player's controls). This is not acceptable, and pretty soon now the client for whom I'm developing this stuff will ask me what possessed me to use Linux rather than Windows... which will be embarrassing, apart from the risk of having to abandon Ubuntu in favor of Windows XP or Vista. <spit>

What can I do to achieve gapless playback of multiple video clips? Please help... :(

---

### Post by rockhopper on 2009-01-22
The following seems to work for me:
```
mplayer -fixed-vo *
```

---

