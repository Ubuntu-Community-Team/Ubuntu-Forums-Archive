---
title: "dodgy playback in VLC / mplayer / kafeiene"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by hamishw on 2007-05-14
Hi
I am using VLC to play video files. I am having a problem with the video playback. I can hear the sound and when I resize the window I can see the video playing but as soon as I let go of the window it seems that the pictures are covered up with a black screen. I have found that if I resize the window in a certain way the picture stays up but as soon as I put a menu up or move the cursor over the screen it goes black again.... Is this a driver problem? HELP!!!

I am using a Dell D 600 lattitude laptop with no windows on it, just feisty fawn.

Many thanks,

Hamish

---

### Post by pognonec on 2007-05-15
I just got the same problem, right after installing desktop effects (7.04). Even after removing the effects, the problem is still there. Before playing with desktop effects, video worked fine... Any suggestion?

---

### Post by pognonec on 2007-05-15
Me again. These forum are sooooo great! I found this, and it solved my problem :) 

For Totem Movie Player:

1. Alt + F2
2. Type "gstreamer-properties"
3. Select "Video" tab
4. In the "Output" line: Choose "X Window System (No Xv)"

For VLC Media Player:

1. Settings>Preferences>Video>Output modules
2. Make sure "Advanced options" box is checked (bottom right)
3. In the "Video output module" line: Choose "X11 video output"

---

