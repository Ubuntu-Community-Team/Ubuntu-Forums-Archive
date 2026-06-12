---
title: "TwinView, XGL &amp; Compiz"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by Paul_G on 2006-08-12
Hi

After much surfing editing and hair pulling I have twin view working, have Xgl installed and working, however when compiz is added into the mix my desktop is forced across the two monitors, so any maximised screen is displayed across my monitors which isn't very helpful.

Anybody had this problem and managed to solve it so they have TwinView, xgl, and compiz all running seamlesly

---

### Post by mkaythe1st on 2006-08-19
Servus,

officially twinview is not yet supported by xgl & compiz. but i got it anyway! its a little bit strange, i think it is a bug in the gdm... 

workaround:

1. set the display from the big resolution/xinerama-mode (in my case 2304x1024) to the small one/single-mode (in my case 1024). 
2. then i got xgl & compiz in single mode. in my case it is the left display. 
3. then i switched back to the big one.
4. then i forced a control+alt+backspace. 

in two of three cases i got xgl&compiz in twinview-mode. it is strange but it works for me! Yeah!!! :p :p :p 

hope it is helpfully
greetz

ps: i start the xgl by the file '.Xsession' my home-folder (in +x mode):

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
exec gnome-session

---

