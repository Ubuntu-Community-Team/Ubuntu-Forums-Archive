---
title: "Issue with 4k TV used as a monitor, won't display correctly under any refresh rate"
date: 2014-11-21
forum: Multimedia Software
---

### Post by cestevez on 2014-11-21
I'll start by saying that I use Ubuntu (and other Linux distros) at work so I'm not a complete stranger to Linux, but I do mainly networking mods and when it comes to video I'm a complete noob. All I know has been from troubleshooting this problem...
I have a 4k LG TV that I use as a monitor and works fine in Windows 7  (I'm dual-booting). The drivers included in the "additional drivers" from the software & updates did not work for me, so I installed the ones from the nvidia website, and those worked fine. No more issues (at 1920x1080@60Hz). When I switched to 3840x2160 I got half of my screen green, with traces of seem to be by desktop, and the other half is completely pink. After 30 seconds or so, everything is back to normal.
I have read that many people have had issues with 4k resolution, but some mention they are missing the option entirely and solve with modeline, others get it working but at low refresh rates, and so on... but I can't find anyone that has experienced the same problem as me.
When I type xrandr I get the following:
[FONT=courier new][COLOR=#000000]
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384[/COLOR]
[COLOR=#000000]DVI-I-0 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]DVI-I-1 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm[/COLOR]
[COLOR=#000000]   1920x1080      60.0*+   59.9     50.0     30.0     25.0     24.0     60.1     60.0     50.0  [/COLOR]
[COLOR=#000000]   4096x2160      24.0  [/COLOR]
[COLOR=#0000ff]**   3840x2160      30.0     25.0     24.0  **[/COLOR]
[COLOR=#000000]   1360x768       60.0  [/COLOR]
[COLOR=#000000]   1280x1024      60.0  [/COLOR]
[COLOR=#000000]   1280x720       60.0     59.9     50.0  [/COLOR]
[COLOR=#000000]   1152x864       60.0  [/COLOR]
[COLOR=#000000]   1024x768       60.0  [/COLOR]
[COLOR=#000000]   800x600        60.3  [/COLOR]
[COLOR=#000000]   720x576        50.0     50.1  [/COLOR]
[COLOR=#000000]   720x480        59.9  [/COLOR]
[COLOR=#000000]   640x480        60.0     59.9     59.9  [/COLOR]
[COLOR=#000000]DP-0 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#000000]DVI-D-0 disconnected (normal left inverted right x axis y axis)[/COLOR]
[/FONT][COLOR=#000000][FONT=arial][FONT=courier new]DP-1 disconnected (normal left inverted right x axis y axis)[/FONT]

As it can be seen, I have 3 refresh rates that should work at 3840x2160, but when I use:
xrandr --output HDMI-0 --mode 3840x2160 --rate 30
I just see distortion, same occurs at 25 and 24 Hz.

If it helps any, what I see is attached. As I mentioned earlier, it works in Windows, so I can only assume it is not a cable or any other hardware issue.

Thanks in advance to anyone that can help.




[/FONT][/COLOR]

---

