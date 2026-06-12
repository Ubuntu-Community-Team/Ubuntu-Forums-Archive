---
title: "Choppy Video in Using Beryl"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by clucas on 2007-03-04
Viewing AVi files while using Beryl the video is choppy. I've used mplayer, kaffeine, gxine. The choppiness isn't much but enough to be disturbing. When I don't have Beryl running there is no problem at all. I have an nVidia card and have no other video issues. Anyone?

---

### Post by panch0 on 2007-03-05
Make sure you are using accelerated video output like XVideo. For example in KPlayer that setting is under Settings - Configure KPlayer - Video. In other programs it should be similar.

---

### Post by StarscreamD on 2007-03-06
I have the same issues after installing beryl using a NViDiA GeForce MX 420. I also use VLC. If I use the default resoultion it is fine, but if I expand the window, the choppiness and pixelation gets bad. I had to go into the video settings and set the video to use the X11. Without this, a black screen was over the video! Should I use XVideo instead..? I will try this and report back soon..

---

### Post by StarscreamD on 2007-03-06
I cannot find a better solution then X11 as your video output. I cannot resize the video window without bad choppiness.

---

### Post by panch0 on 2007-03-07
Have you tried MPlayer? That is what KPlayer uses as the backend.

---

### Post by StarscreamD on 2007-03-07
I've been playing around with alot of settings, and it could be anything from general beryl settings to video settings in vlc to options in the xorg.conf file. Long story short, I was able to tweak my system enough to play the videos to reasonable satisfaction. I still get errors with vlc when i try to minimize and maximize my windows. Also, when my screensaver returns to the desktop, it is completely black save for the cursor. If I right click, everything returns to normal. Kind of strange...
:popcorn:

---

