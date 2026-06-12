---
title: "Dualscreen with Intel x3100 problems"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by aerials on 2007-10-31
I'm having trouble getting dualscreen to work with my intel x3100 graphics chip. I have connected two 1600*1200 lcds to my dockingstation via dvi and vga. I can get it to work dynamically with xrandr when I enter these commands:
```
$ xrandr --output LVDS --off //disables internal laptop screen
$ xrandr --output VGA --auto //?? seems to be necessary
$ xrandr --output VGA --right-of TMDS-1 //activates & positions vga screen
```

These will only last one session. I made a script out of this which works fine, but as soon as I want to watch a video file with Totem in fullscreen mode, I loose all the settings and the vga display.

Does anybody have a clue, how I can make these settings permanently in my xorg.conf? I tried it with this guide: [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) but never got a working solution. Mainly, I am unable to deactivate the internal laptop screen so the vga screen will never be active on startup.

And of course I also tried the new screens and graphics utility in gutsy, but that thing seems to be a oneway ticket to bulletproof x on my system ;)

---

