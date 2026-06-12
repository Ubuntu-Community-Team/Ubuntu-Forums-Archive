---
title: "Open Source Radeon Driver Dual Head Modes and Brightness"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by antipasto on 2007-12-12
Been having some difficulty pinning this down exactly, but I've made great headway, and fixed many other issues without ever having to post, so BIG THANKS to the entire community.

AMD 2500XP (Barton! heheh) ATI Radeon 9700 Pro
Running Gutsy, 2.6.22-14-RT Kernel

Here are the problems I have:

1. When I start up the login (GDM) is kind of low resolution, but that's no biggie.

2. When I DO log in, it doesn't set the video mode correctly or something, and the screen goes blank on the DVI (but the VGA shows the screen)... By Doing a Ctrl+Alt+F9 (or any), and then Ctrl+Alt+F7, and everything is fine (mirrored fine)... this also happens when coming back from power saving mode... move the mouse, the monitor gets the signal and powers back on, but the screen is black until I switch screens and back.

3. The VGA is much brighter than the DVI... I've tweaked it with xgamma but there seems to be more than just brightness, but other curves on each of the colors or something, because its still not right, and the xgamma tweak just makes the DVI darker, too.

I didn't have any of these issues with Fiesty, but its been a chore to get this far since the upgrade. Attached are the xorg.conf and the xorg.0.log...

Anyone have any ideas? I'll try about anything hehe ;p THANK YOU!!!

---

