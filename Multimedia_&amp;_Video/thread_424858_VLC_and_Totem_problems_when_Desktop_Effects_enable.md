---
title: "VLC and Totem problems when Desktop Effects enabled"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by wampirek on 2007-04-27
Hello, 

I have problems using VLC and Totem, when Desktop Effects are enabled. 
Totem doesn't show anything, and VLC sometimes shows the movie, but most of time it only shows black. Sometimes it helps to move player left or right, but when I want to use fullscreen mode, it goes black again. 
When I disable Desktop Effects everything is OK again. 

I do not have these problems with mplayer, but it has problems with screensaver - I will write about it later, with screenshots. 

Is there any way to make VLC play movies when Desktop Effects are enabled? 

Best Regards, 
Wampirek

---

### Post by wampirek on 2007-05-07
Noone knows the answer? I don't believe it ;)

---

### Post by Arif Karim on 2007-05-07
I have the same problem :(

---

### Post by sqela on 2007-05-07
x2

---

### Post by mills on 2007-05-14
X3

---

### Post by lummer on 2007-05-15
me 4

---

### Post by evilc on 2007-05-15
Don't know if this helps but the same is happening to me but when I use SMPlayer if I use double click to make full screen it works, selecting from menu is the same as all others black screen.:confused:

---

### Post by IainT on 2007-05-15
I had the same. Will try it with the new graphics card and see what happens.

---

### Post by circuitsurfer on 2007-05-21
I have the same problem with VLC but Totem works fine.

---

### Post by david_2001 on 2007-05-21
> **circuitsurfer said:**
> I have the same problem with VLC but Totem works fine.

I have an NVidia card, so only know about AIGLX.  Two things to try:
[LIST=1]
[*]In vlc, make sure  "Alternate Fullscreen Method" is NOT checked in the advanced options for OpenGL(GLX) or, just in case, for XVideo.  Be sure to save settings then close and restart vlc before trying again.
 [*]Run gconf-editor and check "unredirect_fullscreen_windows" under / apps / compiz / general / screen0 / options.  This is something that I used to have do when running Beryl.  I haven't needed to with Compiz but it does no harm and might even work.
[/LIST]

---

### Post by CarpKing on 2007-05-24
This is because compositing screws up Xvideo output.  Some players handle it better than others.  Players that use Xine and MPlayer seem to work the best.  You can also disable Xv output, but that uses more CPU and doesn't scale well.

---

### Post by thatcooldude on 2007-06-10
As was discovered in this forum:
[http://ubuntuforums.org/showthread.php?t=428018](http://ubuntuforums.org/showthread.php?t=428018)

You can simply go into VLC, Preferences > Video > Output Modules (make sure "Advanced Options" is checked in the lower right hand corner) and choose X11 output instead of Default.

That should get you video perfectly fine, but it will unfortunately NOT use the video card for rendering the video, and thus quality is lacking, and CPU usage rises.  But it's a temporary fix, for now.

---

