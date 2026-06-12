---
title: "Problem with skewed video playback on ati dualhead setup"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by lmandrake on 2007-02-11
Hello,

I have problems with video playback on my machine. I'm using a Ati 9600XT with the fglrx driver in dualhead mode (DVI 1280x1024 and the other screen VGA 1024x768 ). This works great for my daily application both with kde and gnome. But there are 2 strange things happening with my setup:

1. When the vga screen is not connected i.e. only the dvi connected one and I try to start xine or kaffeine they immediately crash the xserver and bring me back to the login screen. This is not a real problem for me  just annoying ...

2. When I want to watch a video the videooutput of xine, vlc etc is skewed. They all put the output window always to the right size corresponding to the moviesize but the shown movies looks zoomed and therefore truncated. Even in fullscreen playback this is happening. I tried to do a screenshot but sadly the outputwindow is always captured black ... hope you unterstand what I mean.

Does anybody have an idea what exactly is happening there? Maybe it's related to the 2 different screensizes but I can't understand why this should not work properly.

xorg.conf and xvinfo output attached

Greetings
lmandrake

---

