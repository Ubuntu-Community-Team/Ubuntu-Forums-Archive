---
title: "black screen every 10 minutes on playing video"
date: 2008-04-29
forum: Multimedia Software
---

### Post by the1417 on 2008-04-29
hi everyone, i need help. every time i play video file (vcd, dvd, mpg, wmf, avi, etc...) with video player (totem, gxine, mplayer, and vlc) the screen **always** goes black every 10 minutes. audio still there but not video. what i was done are :
1. set screensaver to 2 hour and disable
2. power management are disabled
3. power management and screensaver process ended or killed
4. in gconf, totem > plugin section screensaver is uncheck
5. power management in BIOS is disabled
6. compiz-fusion are enable or disable still got the problem

so please i need help verymuch:(. i cant enjoy watch the  movie because i must move the mouse every 10 minutes. thank you before everyone.

---

### Post by BlueSkyNIS on 2008-05-17
Well, many users are having this problem (including me also)


I have found some similar threads, but no solution: :(
[*[SOLVED] Monitor goes to sleep while playing DVDs*]("http://ubuntuforums.org/showthread.php?p=4980569")
[*screen goes blank after 15 minutes, no screensaver/power management*]("http://ubuntuforums.org/showthread.php?t=719314")
[*Power management Issues*]("http://ubuntuforums.org/showthread.php?t=702877")
[*Disable xscreensaver while playing movie*]("http://ubuntuforums.org/showthread.php?t=691560")
[*screen turning off when watching movies?*]("http://ubuntuforums.org/showthread.php?t=187313")

:confused:
Does anyone have an solution? :confused: :(

---

### Post by the1417 on 2008-05-31
i guest this problem will never solved. before i get more frustated i has change to kde base distro and no problem.

---

### Post by Supergibbon on 2011-06-17
In terminal:

$ gconf-editor

Go to: Apps>Gnome-Screensaver and adjust Idle-Delay time.

---

