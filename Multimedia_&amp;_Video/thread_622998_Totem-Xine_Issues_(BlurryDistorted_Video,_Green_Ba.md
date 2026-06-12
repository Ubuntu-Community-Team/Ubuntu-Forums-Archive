---
title: "Totem-Xine Issues (Blurry/Distorted Video, Green Bar)"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by CMM on 2007-11-25
Hi all,

There have been a few threads on this issue, but no answers or activity on them for almost year.  So here's my problem:

I'm running 64 bit Ubuntu 7.10 Gutsy with an ATI Radeon Mobility x1400 video card and Totem-Xine trying to play some AVI files.  All but two of the AVI files I have play very well.  The issue is the two problem AVI files playback with distorted video and a thick green horizontal bar about an inch from the top of the screen.

I've ruled out an issue with the AVI files by trying them with VLC (with X11 output) and they played perfectly.  This was the solution I found in one of those other threads, but I prefer Totem and it bothers me that something isn't working.

So far I have deleted my .xine directory and restarted Totem (a fix that worked for someone else in a thread) and tried completely removing/reinstalling Totem and Totem-Xine, but nothing has helped.

I could just remove Totem and set VLC as my preferred app (it won't play my .MP4 files though), but I'd rather everything just work properly.  I might try Totem-gstreamer and see, but everything I read while looking for a solution just seems to indicate if Totem-Xine has a problem with it Gstreamer will only be worse.

Any suggestions?

---

### Post by mdpalow on 2007-11-25
Not sure what you got goin' on in your system after all the playin' around you might have been doing. :)

What not start at the beginning again.

See link in my signature... my script has a utility option for installing all the proper files for totem. Might help in your situation... The script definitely works, but it can't obviously account for other issues outside of drivers and such...

good luck...

---

### Post by oceanfree17 on 2007-11-29
Hi All,

I'm having the same problem with 7.10 and an ATI Radeon x1650. I can use VLC without the issue again using the x11 option but thumbnails & pretty much every other video software causes the same green bar. I didn't have this issue with 7.04.

If anyone can get to the bottom of this it would be really appreciated, or should it be a bug report?

Cheers!

---

### Post by genesis2seven on 2007-12-26
I'm having the same problem. avi files were working great in totem-gstreamer but I couldn't play any of my commercial DVD's and was unable to find a solution to make it work.

I uninstalled totem-gstreamer through Add/Remove Programs and installed totem-xine. Now I can play all my commercial DVD's but every .avi file I've tried to play has the same thick green horizontal line through the middle and then video below the line is very blurry. This is true for both my laptops:

Dell Inspiron 6400, ATI Radeon card
Sony Vaio VGN FS630/W, Intel Integrated Graphics card

Would be great to find a solution for Xine playing avi files as it seems to play many more formats than gstreamer natively and there doesn't seem to be a solution for getting gstreamer to play commercial DVD's that I could find.

 :-\"

---

### Post by heiowge on 2008-07-23
I'm having something similar.

Playing with windows media player - fine
Playing with vlc - thick green bar at the top of the video
Playing with totem - thin vertical green bar just to the right of the middle of the display, then video is severely skewed diagonally like this /

Other files play fine - it's just a few that do that.

Any ideas?

---

