---
title: "4k resolution on intel nuc d54250wyk with 65inch LG 4K TV"
date: 2014-10-09
forum: Multimedia Software
---

### Post by pleasehelpme2 on 2014-10-09
[COLOR=#000000]Hi there, total novice here[/COLOR]

[COLOR=#000000]could anyone help me with my NUC, got an LG 4K tv and struggling to get it running in 4K mode! get the following output using xrandr and trying to follow some comands i have seen online[/COLOR]

[COLOR=#000000]nuc@nuc:~$ xrandr[/COLOR]
[COLOR=#000000]Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767[/COLOR]
[COLOR=#000000]HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm[/COLOR]
[COLOR=#000000]1920x1080 60.0*+ 50.0 59.9 30.0 25.0 24.0 30.0 24.0 [/COLOR]
[COLOR=#000000]1920x1080i 60.1 50.0 60.0 [/COLOR]
[COLOR=#000000]1280x1024 60.0 [/COLOR]
[COLOR=#000000]1360x768 60.0 [/COLOR]
[COLOR=#000000]1152x864 60.0 [/COLOR]
[COLOR=#000000]1280x720 60.0 50.0 59.9 [/COLOR]
[COLOR=#000000]1440x576i 50.1 [/COLOR]
[COLOR=#000000]1024x768 60.0 [/COLOR]
[COLOR=#000000]800x600 60.3 [/COLOR]
[COLOR=#000000]720x576 50.0 [/COLOR]
[COLOR=#000000]720x480 60.0 59.9 [/COLOR]
[COLOR=#000000]640x480 60.0 59.9 59.9 [/COLOR]
[COLOR=#000000]720x400 70.1 [/COLOR]
[COLOR=#000000]DP1 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]HDMI2 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]nuc@nuc:~$ xrandr --newmode "3840x2160" 307.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync[/COLOR]
[COLOR=#000000]nuc@nuc:~$ xrandr --addmode HDMI1 3840x2160[/COLOR]
[COLOR=#000000]nuc@nuc:~$ xrandr --output HDMI1 --mode "3840x2160"[/COLOR]
[COLOR=#000000]xrandr: Configure crtc 0 failed[/COLOR]
[COLOR=#000000]nuc@nuc:~$[/COLOR]

---

### Post by pleasehelpme2 on 2014-10-16
anybody got any ideas on what i should be doing next..

---

### Post by sp40140 on 2014-10-17
few questions: as xrandr shows, does the display run @ full 1080p resolution? Have you tried running this on windows to see if this works? May be you can play with frame rate.. also as remote possibility... some hdmi cables might not support 4k resolution depending on version (below 1.4 and quality)...

---

### Post by tgalati4 on 2014-10-17
Go through the log file:  /var/log/Xorg.0.log.  There are probably a few errors that might be helpful.

```
more /var/log/Xorg.0.log
```

---

### Post by raj18 on 2015-06-11
Hello,
I have the similar setup but mine is 50inch LG. How did you get to display via HDMI? when I connected the NUC there is no display on TV. I connected the NUC to a monitor and loaded 14.04. 

TIA

Ra

---

