---
title: "i810 how to force video resolution"
date: 2008-10-29
forum: Multimedia Software
---

### Post by mitsui on 2008-10-29
Dears Ubuntu's members,
  i've a problem with xorg... I've a lcd tv 42'' that supports 1280x768 and 1360x768. In Windowz I can set all the resolution but in Ubuntu 8.04 (driver i810 and 915resolution installed and setted) i can set successfully only 1280x768. I thing the EDID informations provided by tv are wrong but i can't tell xorg to ignore theyr.
I've setted in /etc/default/915resolution:
MODE=5c
XRES=1360
YRES=768
and started it before gdm.

In xorg.conf i've tried to set modeline (provided by gtf) and to add <Option "IgnoreEDID" "True"> in device section. But the resolution became 1024x768. But if I set 1280x768 it's all ok!
I'm going crazy, my video card is intel 945GM and i use in xorg <Driver "i810">: with <Driver "intel"> I have a black screen..
Is it a video card limitation? There's some option to add in xorg to force a video resolution with i810 driver, even if I could break my tv?!
I would like only to use all the pixels... :-(
Thanks a lot for the help!

---

### Post by aeiah on 2008-10-29
if ignore edid doesnt work then you might have to go down the route of inserting a custom modeline. have you still got windows on your pc? its easy to get linux modelines from a windows app called powerstrip, which you can then insert into your xorg.conf. powerstrip will probably not work at all in wine so you'd really have to have windows available.

additionally, have you tried using 1366x768? widescreen 720p HDTVs actually use this and not 1360x768, but a lot of graphics cards cant manage the extra 6 pixels because of the way graphics cards multiply pixels, but its worth a try. perhaps try it in windows first, and if it works, you could use that modeline if the other one does something weird.

my HDTV, although stating a resolution of 1366x768 refuses to do 1:1 pixel mapping and a lot are the same, but if you're sure it outputs this full resolution under windows then it should be possible under linux, especially with intels graphics drivers which are pretty good under linux.

edit: sorry i didnt see that you'd already managed to get a modeline so a lot of my post may be useless :/

---

### Post by mitsui on 2008-10-30
Thank's a lot for suggestion!
I've tried with Windows but with an other video card.
I'll try with powerstrip and other resolution like 1366x768 instead 1360x768!
I'll post my progress!

---

### Post by mitsui on 2008-11-04
There are news about my tv resolution!
I've to thanks a black-out for my discovery because I've understood if i start my pc without monitor and without tv cable and when pc has started I attach tv cable, the tv resolution is ok.....
Any idea?
It can be caused for my tv connection? It's a DVI-VGA in pc and a VGA connection in the television...
Thanks!


SOLVED!!!:
it's to add
Option "MonitorLayout" "CRT"
in "Device" section

---

