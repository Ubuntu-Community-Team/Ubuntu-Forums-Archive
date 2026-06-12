---
title: "[SOLVED] WMV or dvd playback under player screen"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by billmik on 2008-01-20
anyone have this problem? Using any player totem or others i tried the movie or video plays underneath (bottom) of the video player. Not in the section where it should play has a bluish tint sometimes also. i installed restricted ubuntu extras or gstreamer codecs and i get this problem. Any help?

---

### Post by billmik on 2008-01-21
Ok update
I found when i enable the ati restricted driver this happens if i disable the ati restricted driver the videos play normal again. So now i installed the new ati driver in accordance with this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) 
and all goes well like explained.

Any every time i go for the reboot part after
 Finish the Installation
Now save any open document and reboot your system:

sudo shutdown -hr now

on reboot i get the ubuntu screen with the orange loading line after that the screen goes black and the hard drive light goes out. I tried to ctrl+alt+F1 and nothing happens. All i can do is boot in recovery mode up to the prompt telling me to type something in.

Help Plz I wanna get this right so i can get rid of xp

---

### Post by billmik on 2008-01-22
goto here to see how i fixed this problem

[http://ubuntuforums.org/showthread.php?t=674494](http://ubuntuforums.org/showthread.php?t=674494)

---

### Post by billmik on 2008-01-29
> **billmik said:**
> anyone have this problem? Using any player totem or others i tried the movie or video plays underneath (bottom) of the video player. Not in the section where it should play has a bluish tint sometimes also. i installed restricted ubuntu extras or gstreamer codecs and i get this problem. Any help?

Ok after digging further into this problem i solved it finally. hit alt f2 type gstreamer-properties hit run  goto the video tab,  Under default output select x window system (noXv) then close. Videos play where they are supposed to now

---

