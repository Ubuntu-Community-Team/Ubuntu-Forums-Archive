---
title: "Video Playback too dark after installing nVIDIA driver"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by tj.milligan on 2008-02-28
I recently installed the nVIDIA driver using Envy, since I have an 8800GT and the Gutsy repo doesn't yet support it. Video card acceleration works great (however, I've since disabled "Fusion" support since I've run into so many annoyances with it) with the exception of video playback. In both VLC and Totem, video playback is too dark. The only "fix" I've found is for VLC, when I manually set output from "Default" to "X11 video output". Using this option, video playback is normal and vibrant for VLC only; not for Totem. Also, I'd ideally like to use OpenGL as output, but selecting this option makes VLC crash. Any ideas? This is driving me crazy!

---

### Post by tj.milligan on 2008-02-28
bump

---

### Post by tj.milligan on 2008-02-29
bump again.

Anyone else have this problem? I know I have before--a few versions back on my laptop w/ an embedded Intel graphics chip. At that time, I simply upgraded versions and it has been fixed ever since. I think I have narrowed the issue down to the "output plugin". I just don't know how to fix it for VLC and Totem (the default player). Anyone have any ideas? Also, when I do choose X11 output, brightness is fine but video acceleration is not enabled. I can tell because when I enlarge a movie to say 2x, it becomes horribly pixellated as if the graphics card is not smoothing or anti-aliasing the output. Please help!!!

---

### Post by euthyfro on 2008-03-06
yeah, i'm noticing the same thing totem & mplayer are way to dark even though my monitors brightness is set at it's highest

---

### Post by fabbaz on 2008-03-11
hey!
i had the same problem and think i found a solution - i hope it also works for you guys.
at first you have to start a tool called "multimedia systems selector" - in gutsy it was preinstalled, but i believe it was hidden in the menu editor.
so right click the menu bar in the upper left, go to edit, then make sure "multimedia systems selector" is checked at >system>preferences

there you afterwards can find it - start it:
then go to the video tab: at "default output" 
instead of autodetect try "x window system (no xv)".
when you hit the "test" button, you will see the true colors in the test screen as they are supposed to be. compare it to the other options, and you can see how much darker they are.
well, long story short, after resetting the graphical desktop manager with ctrl-alt-backspace and logging in again, all videos were played with the correct colors and, more important brightness.
i couldn't find a bummer so far, so i hope this also solves your problem.

cu!

---

### Post by Conan on 2008-03-14
Using the official Nvidia Settings app to reset hardware defaults on the X Server XVideo Settings page also works - temporarily. No need for restarting X or anything.

I'm not sure what causes it, but it keeps going back to the old, darker setting, though. A permanent fix would be welcome.

Fabbaz, while your fix does correct the color, it does so by changing to another video backend - one that doesn't have nearly as nice video scaling or performance.

---

### Post by Schitso on 2008-03-22
The Multimedia Systems Selector (gstreamer-properties) method worked perfectly! Thanks a million!

---

