---
title: "where does XFCE / X save corrupted driver/ X-settings in xubuntu?"
date: 2013-08-19
forum: Multimedia Software
---

### Post by egerlach on 2013-08-19
Hi, 

I installed xubuntu 12.04 on a 4 years old server mainboard, worked fine. The first thing  I did was  a click on  Settings -> Display. The screen crashed immediately and claimed "No signal input  ... please check cable". Rebooting doesn't help. After lightdm login the display crashes and I read "No signal input  ... please check cable". In  ps ax  I see that XFCE is started. Where the hell does XFCE / X save  corrupted driver / X - settings? 


thx
Eckard

---

### Post by Toz on 2013-08-19
Xfce stores the display information, as defined from the Display configuration applet, in $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml. Deleting that file should restore it to its defaults.

---

