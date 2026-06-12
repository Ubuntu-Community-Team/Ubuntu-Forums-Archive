---
title: "HDMI problem with resolution"
date: 2014-07-24
forum: Multimedia Software
---

### Post by ihavenokia on 2014-07-24
Hello. I want to use my TV as extended screen of my laptop with ATI/AMD.  I have Ubuntu 14.04 and i can only set up HDMI output on mirror mode,  notebook monitor and TV separately. When i uncheck "Mirror Displays" in  Ubuntu setting and change resolution of Tv i can't get a working image  and the mouse stop working, it only moves and sometimes neither this.  What can i do? Is the problem the swichable graphics (always got big  troubles with that) ? Have somebody a fix for that? Thanks.

---

### Post by Flaggmann on 2014-07-24
try using xrandr and arandr to set up what you want simply. install them with sudo apt-get install xrandr then sudo apt-get install arandr  I found a similar dual display problem to you and they worked for me. I use two smart TV's as monitors (one on PC VGA-1 input and the second on the desktop PC's HDMI output). The VGA native resolution is in the 1300 x whatever range and the hdmi input has a native resolution of 1920x1080. So divide 1920 by 1370 approx and it results in a scaling factor of 1.4. So in order to get both to be 1920x1080 open a terminal and run  "sudo xrandr --output VGA-1 --scale 1.4x1.4" the display jumps and changes to the maximum resolution, however the two displays are overlapped. To fix that then run "sudo arandr"  from the same terminal window. This will open a gui that shows the positions on the screen for both displays. Mouse drag VGA-1 and/or HDMI-1 apart and side by side to get what you want for an extended desktop then click the APPLY checkmark button. and you will have what you want. Only drawback to using this method is if you shutdown or log out you have to redo it on login again. I have tried to get a simple answer in forums before to be able to save the configuration so that it can be permanent on login but so far no simple solution. 

There are tips to use cvt command to get a new modeline for the resolution you want and use xrandr to create and add a new resolution mode howver I have yet to have that approach succeed the way the above method works.
you may have to change the names of the displays to what your system has; just run xrandr by itself, in a terminal window,  with no options with both displays connected and it's results should show you what names for you to use on your system.
hope this helps

---

