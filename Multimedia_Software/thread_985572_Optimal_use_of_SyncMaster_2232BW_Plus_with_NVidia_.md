---
title: "Optimal use of SyncMaster 2232BW Plus with NVidia GT series on Ubuntu"
date: 2008-11-17
forum: Multimedia Software
---

### Post by FFighter on 2008-11-17
Hello folks,

I just bought a new desktop with a NVidia 8500GT video-card (running the default NVidia restricted driver, version 177) and a SyncMaster 2232BW LCD monitor (22'). I'm running Intrepid Ibex on it.

This monitor is awesome and that's why I want to get the most out of it, in other words, optimize Ubuntu (X.org) to use it to it correctly and to its maximum potential.

The problem is, X is a (very) complex piece of software. First thing I did when I had the chance was to change the connection from analog to DVI, I had to add some settings to the Device section of my xorg.conf file though in order for it to work.

The monitor seems to be working fine and its status (in its built-in menu) says it is running in Digital mode, at 64.8Khz 60Hz PN and resolution is 1680x1050. 

The Ubuntu Resolution applet doesn't recognize it though, showing a big UNKNOWN in the monitor rectangle and also wrongly shows 50Hz as the frequency being used. Does anyone know why?

But what I really would like to know is if my xorg.conf seems OK for this monitor/video-card combo. I mean, there are so many settings, params and ways to set up X on Linux, that, I, being a neurotic user, need to know if I did things right, so if you are an experienced Linux/X user or also have a similar monitor/video-card, please, share your experiences and wisdom.

**Here's my xorg.conf: [http://pastie.org/317395](http://pastie.org/317395)**

Thanks in advance!

---

### Post by FFighter on 2008-11-18
*bump*

It would really mean a lot for me if someone could take a look at my xorg.conf and give me a hand on this one!

---

### Post by FFighter on 2008-11-26
**last bump**

I would be grateful if at least someone could explain to me why the discrepancy between the modeline I'm using which specifies 60hz as refresh-rate, and Ubuntu's "Screen Resolution" applet, which shows 50hz. Also, this applet shows the monitor name as "Unknown" - Does anyone know if  there is a specific driver for the Samsung SyncMaster 2232BW ?

Here's a screenshot of my screen res. applet:
[[IMG]http://img370.imageshack.us/img370/1937/screenshotmonitorresoluig3.th.png[/IMG]](http://img370.imageshack.us/my.php?image=screenshotmonitorresoluig3.png)

And here's my xorg.conf: [http://pastie.org/317395](http://pastie.org/317395)

And the modeline I'm using, copied from my xorg.conf (you may check under the "monitor" section)
> Modeline "digital:1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

Thanks,

Marcelo.

---

### Post by psyke83 on 2008-11-26
See [this]("http://ubuntuforums.org/showpost.php?p=6197465&postcount=23") post for an explanation of the misreported refresh rate (and yes, DynamicTwinView is enabled by default, so you must explicitly disable it).

A little off-topic, but [this]("http://www.nvnews.net/vbulletin/showthread.php?t=118088") thread is useful to help improve perfomance.

---

