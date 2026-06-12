---
title: "xrandr and extened desktop"
date: 2008-07-22
forum: Multimedia Software
---

### Post by utab on 2008-07-22
Dear all,

First of all, I hope this is the right place to post this question.

I have an HP compaq 6710b notebook and a compaq 7500 external monitor. When I connect the monitor and start up the notebook. I can see the same screen on the monitor as well. However, the laptop screen is not as clear when it was working standalone before connecting the monitor? What could be the reason for this?

What I want is to be able to use an extended desktop facility so that I do not have to switch between terminals to see different outputs.

I did some reading from this thinkwiki blog:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

lspci | grep Graphics

gives

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I gave a try after reading with 

xrandr --output LVDS --right-of VGA

So I have an extended desktop but there is a problem, the main screen of the computer is on the VGA monitor not on the laptop screen, LVDS. How can configure this and how can I solve the resolution problem on the laptop screen. Also I can turn of the VGA monitor with 

xrandr --output VGA --off

but this does not help with the resolution of the laptop screen, I tried the xrandr manual but I guess I am missing sth easy.

Any help or comments are appreciated...

Thx

---

