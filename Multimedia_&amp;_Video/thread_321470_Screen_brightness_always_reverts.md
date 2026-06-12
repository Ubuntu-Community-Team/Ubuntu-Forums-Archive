---
title: "Screen brightness always reverts"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by enopepsoo on 2006-12-19
Hello all,

I recently got a new computer, but decided to keep my old monitor to save some cash! :rolleyes:   It was always a bit dim.  The problem is, my new computer is perfect, so I wanted to fix the dimness issue.  

Here is where it gets really nasty!  I am using the binary nvidia driver [-( (I know, shame on me etc).  It comes with a utility that alters the brightness and all sorts of other neat stuff.  The problem is that when I leave the computer for a while, the screen saver will come on, and I guess the switch of video modes reverts the old brightness settings.

Simply reloading the nvidia configurator solves the problem, so I have an icon for it on my bar at the top.

I was wondering, does anyone know a way that I wont have to load the config tool every time I unload the screen saver?  Maybe the little annoyance is a suitable punishment for not using the free driver.:mrgreen: 

I am not really expecting an answer here to be honest, because I think that my workaround is really outside of normal computer usage.

---

### Post by enopepsoo on 2007-01-03
I figured this one out... If anyone else has a similar issue, you can set up an icon on your task bar that runs this command:
[PHP]/usr/bin/nvidia-settings -l[/PHP]
the -l switch makes it load the configuration without opening the gui configuration tool.  :D

---

