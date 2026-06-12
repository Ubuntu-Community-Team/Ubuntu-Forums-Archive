---
title: "xrandr - TV Out Settings for CRT - modeline?"
date: 2011-09-05
forum: Multimedia Software
---

### Post by jbartosh on 2011-09-05
Hello, hope someone has some experience or help in setup for something like this.  I'm trying to setup an old TV - A Sanyo DS32224 CRT.

I've been tweaking with xrandr setting up a modeline as the following:

"720x480_29.97" 13.5 720 736 799 858 480 486 492 525 Interlace

This actually makes the viewing worse than the default (which I believe is a 800x600x50)  This is all out of the TV-1 output.

My symptoms are a black & white screen that rapidly "scrolls".  At best, I can get a little purple color mixed in there.  I'm pretty sure it's just a matter of telling xrandr what to do because the BIOS screen lights up in full color with no scrolling affect perfectly~!

Please contact me with any suggestions on a modeline or how to tweak settings in.

---

### Post by jbartosh on 2011-09-05
I wanted to add, I changed the refresh rate to 60 instead of 29.97 based on info I found via Google for my TV.  No help as of yet.  Color still out too.  Is there a way to change the color profile via xrandr for generic CRT TV settings?  I would think the "scrolling" I'm seeing is because of refresh rate, but maybe not - whatever I try nothing seems to work.

---

### Post by jbartosh on 2011-09-05
Updating as I'm working here.  I've gotten very close to a solution by setting TV standards like this:

$ Xrandr - output TV-1 - off 
 [LEFT]$ xrandr --output TV-1 --set mode NTSC-M[/LEFT] $ Xrandr - output TV-1 - set mode NTSC-M 
 [LEFT]$ xrandr --output TV-1 --right-of VGA-1 --mode 640x480[/LEFT] $ Xrandr - output TV-1 - right-of VGA-1 - mode 640x480 

The last line I'd like to come up with a solution to turn on the TV-1 output without making it to the right of the VGA monitor.  Anyone know how to do this?

Anyway, this works except every 5 seconds the screen "blinks" out to black for a 1/2 second then comes back.  This repeats continually.  Refresh rate issue?  Any ideas?

---

### Post by BicyclerBoy on 2011-09-06
The blinking/blanking out is probably from the TV losing sync, so the video mode is likely not right.
Any old CRT I once had worked with 1024x768 & 800x600 interlaced.

CVT calculates..
Modeline "720x480_29.97"   13.50  720 744 808 896  480 483 493 512 interlace -hsync +vsync

This is actually 720x480i60.

Are you using intel graphics ?

---

