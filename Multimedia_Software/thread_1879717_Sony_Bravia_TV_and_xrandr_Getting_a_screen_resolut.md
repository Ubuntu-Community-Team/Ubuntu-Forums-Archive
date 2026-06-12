---
title: "Sony Bravia TV and xrandr: Getting a screen resolution"
date: 2011-11-12
forum: Multimedia Software
---

### Post by wannabegeek on 2011-11-12
Hi all,

I have been setting up my new and first ever build, of my second media server machine running Ubuntu 10.10 on a Asus P8H67-m PRO MOBO with an i3 CPU and 4 GB 1600 DDR3 RAM. I would have gotten cheaper RAM but it worked out since it was cheap anyway and on the QVL.

I have a funky older Sony Bravia KLV S32A10  TV and had a time learning to get a working screen resolution when using the HDMI inputs.

I think there is still something wrong, since when I move a windows around quickly, there's a redraw lag,
but that may well be a different issue.

Pull the working modeline from the xorg log at  /var/log/Xorg.0.log

Adjust the screen dimensions width and height, then translate the image to the center.
Follow this guy's idea, but do not mess with the sync times, just the scale and translation.

[http://www.mythtv.org/wiki/Working_with_Modelines](http://www.mythtv.org/wiki/Working_with_Modelines)


If you screw up a setting,  you can always go to tty1, CNTL-ALT-F1 and restart gdm/kde  from there.

Here's my current modeline, which is not from gtf, this is custom.

"1200x680" 74.25 1200 1390 1300 1650 680 725 705 750 +hsync + vsync

cheers !
wbg

UPDATE:  changed my modeline
"1215x680" 74.25 1215 1390 1300 1650 680 725 705 750 +hsync + vsync

Window redraw is choppy and my TV keeps displaying the input mode and resolution, which is a bad thing. I tried Ubuntu 11.10 from LIVE CD
and the window redraw issue seemed to go away. I suspect that 11.10 has better video drivers for my MOBO's Intel integrated chip.

Going to try a dubious copy of Windows7 and see what happens.

---

### Post by Paddy Landau on 2011-11-14
I haven't used xrandr since 8.04. Have you tried the Monitors application (under the System menu on 10.10)? It's much easier.

If you are getting laggy problems, it could be that the driver is not suitable (which could explain why 11.10 works better, as it has more up-to-date drivers), or your graphics card may not be quite up to what you are asking from it.

---

### Post by wannabegeek on 2011-11-14
11.10 did fix my window redraw issue....the monitor gui doens't help, since the TV is reporting a resolution that is not
correct for some reason...the myth help pages mention it  somewhere....

Things are working pretty good now....just one more annoying issue which may not have a cure....I started another thread for that....

I'm marking this solved....thanks forum...
wbg

---

### Post by Paddy Landau on 2011-11-15
Good, I'm glad you managed to solve it.

---

