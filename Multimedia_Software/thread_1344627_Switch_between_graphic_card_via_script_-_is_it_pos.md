---
title: "Switch between graphic card via script - is it possible ?"
date: 2009-12-03
forum: Multimedia Software
---

### Post by Chareos on 2009-12-03
Hi guys,

trying to make a good purchase, I'm looking for a new notebook.
Of course, the hottest are those with 2 videocards, and you can switch between them
(that'd be called Hybrid SLI for nVidia, for example, but Asus have another name for that)

Now, I understand that real-time videocard switch won't work on linux, so I'm thinking about alternatives.


THE QUESTION
In your opinion,
would be possible to make a script that changes/replaces/modifies xorg.conf to make use of the selected videocard AND restarts the graphic environment ?

Or, safer, a script that makes the change to xorg.conf AND puts an ubuntu-notification like "Next login will make use of XXX videocard" ?

Another question
I read somewhere that the excluded videocard may stay on. Via script, wouldn't be possible to issue the same mechanism used to power off videocard in suspend mode, for the non-chosen card ?

Thank you for your toughs.

---

### Post by Chareos on 2009-12-14
Don't tell me I've to give a chance to windows 7...
I'd rather cut out my own right arm !

---

### Post by Martins2040 on 2010-02-09
im all ears, i wanna hear about this too if getting real. I got a laptop with 3 cards, 1 slowpoke office and 2xnvidia running SLI in windows...not in linux. IF able to run with just 1 of em would be nice...

---

### Post by efflandt on 2010-02-10
X tends to start dual displays in a common mode that they both can handle (like 1024x768 ).  This is an example of a script for my laptop (standard modules/drivers) that sets up a 1080p mode, turns off laptop display, and switches its VGA to 1080p.

You can put that in a ~/bin directory (which will be added to your PATH when you relog into X).  Then I put a launcher on the desktop to run that (double click) in a terminal when connected to external display.  However, your devices used for this may vary if using a different video card (see what **xrandr** lists).  Also see **man xrandr** and [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

```
#!/bin/bash
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00
exit
```

---

