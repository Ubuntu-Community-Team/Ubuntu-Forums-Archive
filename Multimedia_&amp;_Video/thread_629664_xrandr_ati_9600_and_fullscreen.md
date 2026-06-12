---
title: "xrandr ati 9600 and fullscreen"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by d3ni5 on 2007-12-02
I'm using ati 9600 with open source "ati" driver.
My ati 9600 has 2 interfaces - DVI and VGA.

I connected:

-monitor to VGA 
-Plasma panel to DVI via HDMI


I succefully can mange my screen config with xrandr (since xinerama and mergedfb is not supported anymore).

The problem: if I try to watch video in fullscreen - the video is moved to VGA screen, Plasma is Black Screen and no way to reactivate plasma screen except restar Xserver.

---

### Post by sharris203 on 2007-12-10
I have a similar problem (although I use intel graphics drivers). SOMETIMES the fullscreen video does work properly. But usually it does not. If it messes up, I use the command below to easily fix the monitor placement. However, this still does not stop them from messing up a 2nd time. At least I don't have to restart X though. My two inputs are VGA (external monitor) and LVDS (laptop screen). I put this command:

xrandr --output LVDS --auto --below VGA

into a script file, and placed a link on my panel bar. One click for an eaxy fix. You can modify that to fit your needs.

To get around the fullscreen problem, in Totem, I 'maximize' the program, and turn off the menus (shortcut = h key). It's 95% fullscreen except you'll have a title at at the top.

---

