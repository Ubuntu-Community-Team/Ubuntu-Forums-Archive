---
title: "How to add 320x200x8 Resolution/Mode to xorg.conf???"
date: 2010-10-01
forum: Multimedia Software
---

### Post by travlemon on 2010-10-01
Hey everyone,

I'm hoping this is a quick and easy answer.  I have  an old, nostalgic dos game that I am trying to run using WINE.  It has a  platinum rating on the site, and runs perfectly on my laptop.  However,  on my desktop it doesn't seem to run at all.  The screen goes black,  then brings me back to the desktop.  I manually ran the WINE command in  the terminal, and it produced the error  "err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found  320x200x8
@0! (XRandR)".  The laptop and desktop are both running the  same version of WINE (1.3.3) and have similar Nvidia cards (laptop has a  mobile 9600, desktop has a 9800).

I found a bug report on this  exact issue on the WINE website (I'll paste a link), and they mention  that the solution is simply to add the 320x200x8 resolution mode to  Xorg.conf.  

My question is simply, how do I do that?  I've been  Googling, and I can't really seem to find a definite answer.  I've tried  generating the line that I may need with a web-based modeline  calculator, referenced on another thread, but it caused my system to  fail booting.  Luckily, I backed up xorg.conf before making changes and  restored the old one via recovery mode. Here's the link to the  calculator, I may just be using it wrong:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Any help on straightening out my workflow would be much appreciated. Thanks in advance!

---

### Post by travlemon on 2010-10-03
> **travlemon said:**
> Hey everyone,

I'm hoping this is a quick and easy answer.  I have  an old, nostalgic dos game that I am trying to run using WINE.  It has a  platinum rating on the site, and runs perfectly on my laptop.  However,  on my desktop it doesn't seem to run at all.  The screen goes black,  then brings me back to the desktop.  I manually ran the WINE command in  the terminal, and it produced the error  "err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found  320x200x8
@0! (XRandR)".  The laptop and desktop are both running the  same version of WINE (1.3.3) and have similar Nvidia cards (laptop has a  mobile 9600, desktop has a 9800).

I found a bug report on this  exact issue on the WINE website (I'll paste a link), and they mention  that the solution is simply to add the 320x200x8 resolution mode to  Xorg.conf.  

My question is simply, how do I do that?  I've been  Googling, and I can't really seem to find a definite answer.  I've tried  generating the line that I may need with a web-based modeline  calculator, referenced on another thread, but it caused my system to  fail booting.  Luckily, I backed up xorg.conf before making changes and  restored the old one via recovery mode. Here's the link to the  calculator, I may just be using it wrong:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Any help on straightening out my workflow would be much appreciated. Thanks in advance!


After a bit of research, I managed to find out that running the command "xrandr" will display a list of all resolutions supported by your video card.  

The answer is simply...my card surprisingly doesn't support it.  For any onlookers who receive this error when trying to run some of your favorite Windows based oldschool games via Wine, try running it in the terminal to see if you get any useful error messages.

---

