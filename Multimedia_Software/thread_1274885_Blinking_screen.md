---
title: "Blinking screen"
date: 2009-09-25
forum: Multimedia Software
---

### Post by BOZO1 on 2009-09-25
Hi all, I am new in ubuntu. I have installed ubuntu 9.04 and it did like a charm.some bugs  were resolved through the ubuntu forums.

Currently i have a "blinking" screen(every 2secs) when hook my pc to my lcd philips tv through an hdmi/hdmi cable. I tried messing with the nvdia control panel, etc/X11/xorg.conf file but nothing came out. (When the pc is connected to crt monitor everything is just fine.)

I have read in other forums that it has to do something with the nvidia driver for linux. I am using the 180 version of the driver , installed through the hardware drivers manager.

I saw that nvdia had released 185 version for linux drivers, but i can not manually  install it.It is  a .run file.I searched the forum how to  install it , but couldn't get it  installed.Not much an ubuntu savvy.

I really want to use the pc with my tv, as this would be perfect. I am thinking of installing karmic koala in late October, perhaps this will resolve the issue.

I don't know what to do , please help :(

---

### Post by BOZO1 on 2009-10-09
After a lot of googling around i came across the following posts that are related to this matter. To be frank what i did is, i opened terminal and typed the command  : 
*[FONT=&quot]while true; do glxinfo > /dev/null; sleep 5; done [/FONT]*
and it seems to settles the blinking.I will test for a whole day it though and revert.

[http://ubuntuforums.org/showthread.php?p=3574946#post3574946](http://ubuntuforums.org/showthread.php?p=3574946#post3574946)
[http://www.astroshapes.com/information-technology/blog/archives/29-ubuntu-7.10,-nvidia-and-screen-flickering.html](http://www.astroshapes.com/information-technology/blog/archives/29-ubuntu-7.10,-nvidia-and-screen-flickering.html)


:lolflag:

---

