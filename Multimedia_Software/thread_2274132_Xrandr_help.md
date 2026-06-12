---
title: "Xrandr help"
date: 2015-04-18
forum: Multimedia Software
---

### Post by borut2 on 2015-04-18
Hi ,

Im trying to connect my laptop with TV using xrandr ,but i always get 4 splited screens ,same with lxrandr

[COLOR=#333333][FONT=monospace]> xrandr --auto

[/FONT][/COLOR][[IMG]http://shrani.si/t/38/DU/4hcWEf4j/0.jpg[/IMG]]("http://shrani.si/?38/DU/4hcWEf4j/0.jpg")

> [COLOR=#444444][FONT=sans-serif]xrandr -q[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   1366x768      59.94*+[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   1024x768      60.00  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   800x600       60.32    56.25  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   640x480       59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]DP1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]HDMI1 connected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   1920x1080i    50.00 +  60.00    59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   1280x720      60.00    50.00    59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   720x576       50.00  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   720x576i      50.00  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   720x480       60.00    59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   720x480i      60.00    59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]   640x480       60.00    59.94  [/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]VGA1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR][COLOR=#333333][FONT=monospace]


[/FONT][/COLOR]

---

### Post by dino99 on 2015-04-18
which ubuntu is used ? which graphic is used ? which tv port is used ?

usually the kernel is able to identify the hardware and then choose/set the correct settings for you. Often xorg.conf disturb the default's kernel choice and then set a worst result, so remove xorg.conf

---

### Post by borut2 on 2015-04-27
I have laptop Sony Vaio ,so Intel graphic I want to connect to HDMI1 
Running Ubuntu 15.04 i3wm
I dont have xorg.conf

---

### Post by dino99 on 2015-04-27
ok, let us see what 'sudo journalctl' report as error(s) (red lines), and xorg.0.log

[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

---

