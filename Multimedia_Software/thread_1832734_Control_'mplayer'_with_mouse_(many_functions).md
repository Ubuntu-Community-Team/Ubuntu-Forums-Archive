---
title: "Control 'mplayer' with mouse (many functions)"
date: 2011-08-25
forum: Multimedia Software
---

### Post by Dr_Frost on 2011-08-25
Just wanted to share what i just got working (yes pretty low level), this is for my MEDIA PC, really only use it to see video and i wanted to omit the keyboard, when using mplayer without GUI then normally you will use LEFT, RIGHT, UP, DOWN, PgUp, PgDn to skip and so on.

In my setup i now only use the mouse for this PC, a stock logitech mouse (left, right, scroll & middle click).

Explaining of the functions:

Standard stuff:
Double click left = Full screen
Single click right = pause/play
Single click middle = OSD time progress
Scroll wheel = Volume -/+ 2

Extra good stuff:
Hold right & double click left = Quit
Hold left & scroll = seek -/+ 5 sec
Hold right & scroll = seek -/+ 30 sec
Hold middle & scroll = seek -/+ 300 sec (5 min)

The hold right & double click left is a nice touch so it is not needed to put the video out of full screen (double click left) and closing it there

The Files:
[B]input.conf
[/B]```
MOUSE_BTN2 pause
MOUSE_BTN1 osd_show_progression
MOUSE_BTN0_DBL vo_fullscreen

MOUSE_BTN2-MOUSE_BTN0_DBL quit

MOUSE_BTN3 volume 2
MOUSE_BTN3_DBL volume 2
MOUSE_BTN3-MOUSE_BTN3_DBL volume 2
MOUSE_BTN4 volume -2
MOUSE_BTN4_DBL volume -2
MOUSE_BTN4-MOUSE_BTN4_DBL volume -2

MOUSE_BTN0-MOUSE_BTN3 seek +5
MOUSE_BTN0-MOUSE_BTN3_DBL seek +5
MOUSE_BTN0-MOUSE_BTN3-MOUSE_BTN3_DBL seek +5
MOUSE_BTN0-MOUSE_BTN4 seek -5
MOUSE_BTN0-MOUSE_BTN4_DBL seek -5
MOUSE_BTN0-MOUSE_BTN4-MOUSE_BTN4_DBL seek -5

MOUSE_BTN2-MOUSE_BTN3 seek +30
MOUSE_BTN2-MOUSE_BTN3_DBL seek +30
MOUSE_BTN2-MOUSE_BTN3-MOUSE_BTN3_DBL seek +30
MOUSE_BTN2-MOUSE_BTN4 seek -30
MOUSE_BTN2-MOUSE_BTN4_DBL seek -30
MOUSE_BTN2-MOUSE_BTN4-MOUSE_BTN4_DBL seek -30

MOUSE_BTN1-MOUSE_BTN3 seek +300
MOUSE_BTN1-MOUSE_BTN3_DBL seek +300
MOUSE_BTN1-MOUSE_BTN3-MOUSE_BTN3_DBL seek +300
MOUSE_BTN1-MOUSE_BTN4 seek -300
MOUSE_BTN1-MOUSE_BTN4_DBL seek -300
MOUSE_BTN1-MOUSE_BTN4-MOUSE_BTN4_DBL seek -300
```[B]

config [/B](not nessarry but thought i would throw it in here)
```
ao=sdl
vo=xv
fs=0
geometry=100%:100%
xy=600
ontop=1
```And a quick explaining on the **config**:
ao=sdl (use sdl as audio output)
vo=xv (use xv as video output)
fs=0 (set to 1 for start in full screen)
geometry=100%:100% (start the video in the bottom right corner)
xy=600 (set video width to 600, hight is dependent on aspect)
ontop=1 (set video to be 'Always on top')


If you are not into how the whole mplayer thing works (new to ubuntu), then here is a short explanation:
The 2 files **config** & **input.conf** goes in your /home/ (your user name) /.mplayer
To start video's with mplayer:
Right click on video file (nautilus)
Select Properties
Under 'Open With' tab select Add
Select 'Use a custom command'
Type in '**/usr/bin/mplayer**'
and that's it for that file type (video type), do the same if you open a video and it does not open in the no GUI window in the corner.

---

### Post by Dr_Frost on 2011-09-18
Was tweaking and found that SDL audio was faster and when using the command '/usr/bin/mplayer' instead of just 'mplayer' seeking is wicked fast.

---

