---
title: "Dual Monitors:  How to make programs open on a selected monitor by default??"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by ll0ll0ll0 on 2007-12-08
anyone know how to fix a program so it launches on the monitor you choose instead of always launching on the first screen?

---

### Post by sirdilznik on 2007-12-08
I have a dual widescreen setup with NVIDIA Twin View.  I too have noticed that some programs like to start on certain screens.  For example MythTV always comes up on my primary display(which I'm fine with) while mplayer always comes up in the secondary screen(I would prefer the primary screen).  Most other programs will open up on whatever screen my mouse pointer happens to be on at the time it opens.  I too would like to know how this behavior can be changed.  I'm not sure if it would be different on my computer since I'm running Fvwm.

---

### Post by chronographer on 2007-12-09
I can use DISPLAY=:0.0 or DISPLAY=:0.1 to set whether something runs on screen 1 (0.0) or 2 (0.1) if that makes sense?  SO I can use "DISPLAY=:0.1 vlc movie.avi" and the movie will play on my tv, also I set crontab to run "DISPLAY=:0.0 deluge" tpo start a bittorrent program on my main screen automagically.

Hope this helps

---

### Post by MrHippocampus on 2007-12-09
You could look into using Devilspie for doing this, it involves a bit of editing text files but with a bit of work it should get you what you want, a nice intro to it is [here]("https://help.ubuntu.com/community/Devilspie").

---

### Post by ll0ll0ll0 on 2007-12-13
ok, looks like the only solution i have found is to add quicklaunch icons to the toolbar on the second monitor.  this results in the program opening on the monitor that has the icon on it.

---

