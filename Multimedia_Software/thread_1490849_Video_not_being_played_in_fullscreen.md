---
title: "Video not being played in fullscreen"
date: 2010-05-22
forum: Multimedia Software
---

### Post by sunnyengineeer on 2010-05-22
Hello,
          I'm using Ubuntu10.04 ,Im facing a small problem that,Almost all of [COLOR=Red]my videos are not being played in fullscreen, infact they cover merely around 20% of the screen area[/COLOR],I've tried many player...
VLC,SMPlayer,kaffeiene,Real....but to no avail,,,
     Can somebody plz help me out of this situation..

Thnx
Sunny Sharma

---

### Post by xzero1 on 2010-05-22
With mplayer or smplayer use the -x -y parameters where x is your screen width and y is your screen height. If the video is still to small, you may want to crop it before displaying it with -vf crop=x:y.

As an example, I might use:
mplayer -x 1680 -y 1050 -vf crop=504:368 dvd://

..for playing a particular dvd on a 1680x1050 screen.

---

### Post by sunnyengineeer on 2010-05-22
Hello,
       Thnx for replying & helping tme me to solve this problem.
Regards
Sunny Sharma

---

