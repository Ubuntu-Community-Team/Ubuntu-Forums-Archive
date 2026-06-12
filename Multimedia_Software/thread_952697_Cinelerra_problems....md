---
title: "Cinelerra problems..."
date: 2008-10-19
forum: Multimedia Software
---

### Post by rm2011 on 2008-10-19
Hi,
I am pretty new to linux, but I installed Cinelerra yesterday, and have never been able to get it to really work right.  When I am previewing the video, the audio does not match up with the video, when I am previewing the video, the "time" is nowhere near accurate.  For example if I set a picture to be displayed for 10 seconds according to the timeline it lasts about 30 seconds when I am previewing it.  The audio is playing at normal speed though. After rendering the problem is fixed, but it is almost impossible to synchronize the audio with the video while editing.  Any suggestions?  :confused:

---

### Post by mildred on 2008-12-11
Probably, cinelerra can't play the video as fast as it should be. Perhaps you should enable frame dropping in the preferences.

Settings -> Preferences -> Playback -> Video Out
disable “play every frame” checkbox.

You can also see the maximum framerate that it could achieve. Perhaps you can choose also an accelerated video driver (X11-XV or X11-OpenGL for example)

---

### Post by faintscrawl on 2009-03-19
My syncing problem is after I render. The audio is totally off.

---

