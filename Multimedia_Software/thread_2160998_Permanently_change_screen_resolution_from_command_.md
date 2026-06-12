---
title: "Permanently change screen resolution from command line"
date: 2013-07-09
forum: Multimedia Software
---

### Post by imihajlov on 2013-07-09
Hi folks!
I have ubuntu 12.04 and I need to change screen resolution from my script. Now I do it with xrandr, the resolution changes OK, but only until next reboot.
How can I make this change permanent? Where do the display settings manager store its data?

---

### Post by ohnonot on 2013-07-10
with arandr, you can save your settings to a script that can be called at login (with: startup applications -> create new entry).
you might have to install arandr first.

please call back if that doesn't help or i wasn't precise enough!

---

### Post by ana551 on 2013-07-11
You can either use the Screen Resolution GUI  tool to experiment with different resolutions, or the more powerful  xrandr command-line tool. Without parameters, xrandr shows you the names  of different outputs available on your system (LVDS, VGA-0, etc.) and  resolutions available on each: 

[LIST]
[*]
$ xrandr Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1400 VGA disconnected (normal left inverted right x axis y axis) LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 286mm x 214mm    1400x1050      60.0*+   50.0   [...]
[/LIST]
You can direct xrandr to set a different resolution like this: 

[LIST]
[*]
$ xrandr --output LVDS --mode 1024x768
$ xrandr --output VGA1 --mode 1024x768
[/LIST]
The refresh rate may also be changed, either at the same time or independently: 

[LIST]
[*]
$ xrandr --output LVDS --mode 1024x768 --rate 75
$ xrandr --output VGA1 --mode 1024x768 --rate 60
[/LIST]
Note that changes you make using xrandr only last through the current session.  xrandr has a lot more capabilities - see man xrandr for details.

---

### Post by CatKiller on 2013-07-12
> **imihajlov said:**
>  Where do the display settings manager store its data?
~/.config/monitors.xml

---

