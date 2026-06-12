---
title: "Vlc player - slow in fullscreen?"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by jamienos on 2007-03-10
When i play movie files in vlc, they are really small like 100x100 size which isent really a problem because i play them in fullscreen - only when i go in fullscreen the video seem's really slow

i did try mplayer but when running my videos in there they did not even show only the sound, and when they did they were also slower then vlc when in fullscreen

im useing ubuntu 6.06 and berly 0.2 svn - i think it is something to do with codec's of beryl? i tryied useing diffrent codecs and they just broght up VO errors, and vlc i couldent see anywhere to choose one

thanks.

---

### Post by chewearn on 2007-03-11
Some people suggest using X11 as the video output module for VLC when running Beryl (you can change this in the VLC -> Preferences -> Video -> Output modules).

In my case, it didn't work, and I have to disable Beryl when playing a video.

---

### Post by panch0 on 2007-03-12
What do you get if you run

mplayer -vo xv movie.avi

in the console? If it doesn't work, post the output you get.

---

### Post by juanitobanana on 2008-07-12
Hey Jamienos,

I had the same problem as you (probably because I have a 3 or 4 year old computer, is it the same with you?) and I solved it by putting the value in VLC->Preferences->Video->Output modules->OpnGL-PenGL sampling frequency at its maximum 10 (you need to enable Advanced options)

let me know if this works, it would be my first "problem" solved!

cheers

---

