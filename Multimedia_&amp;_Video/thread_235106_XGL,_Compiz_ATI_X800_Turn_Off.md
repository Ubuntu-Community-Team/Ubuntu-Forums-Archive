---
title: "XGL, Compiz ATI X800 Turn Off"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by Dropknee on 2006-08-12
There is a way to turn off XGL, Compiz without to log out??? a script or something???

thx

---

### Post by Dropknee on 2006-08-13
pls someone :(

---

### Post by sirclaudio on 2006-08-14
Check this [thread]("http://www.ubuntuforums.org/showthread.php?t=174233"), see the step 4a

---

### Post by sirclaudio on 2006-08-15
OK, here's something that combines the thefuture script with the one from that thread:

> 
#!/bin/bash

if ps -A | grep -e " compiz.real$" > /dev/null; then
        killall cgwd
        metacity --replace &
else
       gnome-window-decorator --replace &
       compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
       cgwd --replace &
fi


Now you can do as i did, in the panel add a personal starter, choose this script and put the compiz logo (/usr/share/compiz/logo24.png). Starting or stoping compiz is now a click away...

---

### Post by Dropknee on 2006-08-16
Ok this Work great, but now........ any scrip to get XGL back??? 

I just want this to have some flexibility when I want to play games.

thx

---

### Post by Dropknee on 2006-08-16
sorry my bad but this dont work is I want to play with Cedega,or any other game, need to log-out and log-in in normal gnome . But Thx anyway :D

---

