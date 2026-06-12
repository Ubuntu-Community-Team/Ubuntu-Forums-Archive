---
title: "dual monitor issue, xrandr won't restart after --off"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by mtacqua on 2007-12-13
I am using 7.10 in a inspiron 1720 w/ a GM965 intel card.  If I startup with the TV plugged into the Svideo plug I get a cloned desktop.  (But the menu bars on the laptop are moved and shrunk to accomadate the TV).  I set up a hot key to make an extended desktop using xrandr --output TV --left-of LVDS --auto.  One issue I am having w/ this is it moves the menu bar to the TV, I can then drag it back to the laptop.  Is there a command I can give it to keep it on the laptop screen.  

I have another hotkey to turn the TV off (xrandr --output TV --off).  Once I do this I cannot reconnect to the TV.  I use xrandr --auto, which I thought was suppose to detect any monitors/TVs.  The TV flickers, but the output never returns to the TV.  Am I doing something wrong, or do I need to restart everytime I turn the TV off with xrandr, in order to get output back on the TV?

---

### Post by dysphasi on 2008-01-06
For the menu bar dooda, I have set things up as explained on [this page](http://ubuntuforums.org/showthread.php?t=583566)

The script I use also allows me to use just the one button to cycle through the display options.

One BIG annoyance is that the icons on the gnome panel get shuffled about a lot doing this. 

I gather it's to do with the fact that any external device when activated via xrandr is considered to be the 'primary monitor', hence the panel gets moved, and squashed to fit onto the external display.The panel is shocking at setting and keeping icon positions so they get moved about (pray for an update!).

A further issue is that when one restarts, the settings last used for xrandr are forgotten, so a startup script must be set to run via 'sessions'.

If you or anyone else finds a better way of doing thing pray tell me!

[color=blue]nb. Personally I MUCH prefer dual-head setups, allowing 2 independent screens, I've got this kind of setup on my desktop/NVIDIA 7600gt, MUCH better, with better options for overscan etc... unfortunately I can't find a way to get dual-head with an intel 945gm/gutsy, don't know if your card would allow this, might be worth a try [/color]

---

### Post by mtacqua on 2008-01-07
I followed your link and added "gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1" after "xrandr --output TV --left-of LVDS --auto" and it moves the menu bar without me having to drag it.  Thanks for the help.  I tried your script and it appears it would work, but I have one issue.  If I turn the TV off w/ xrandr it will not turn back on.  So I ran your script w/ the TV on and it turned the TV off.  Then I went to run it again and it would not turn the TV back on.  In order to have the TV on, I must logon to Linux with the TV plugged in, which results in clone monitors then I use "xrandr --output TV --left-of LVDS --auto" to make separate screens and "gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1" to return the menu bar onto the laptop screen.

---

