---
title: "Intel X3500 HDMI video output resolution problems"
date: 2010-02-20
forum: Mythbuntu
---

### Post by bwooster0 on 2010-02-20
I am using Mythbuntu 9.10. I've connected it to my Sony KDS-R60XBR1 via the Intel X3500 HDMI port. I get a screen resolution of 720x480. I want a screen resolution of 1280x720.

xrandr only reports that the HDMI port can do 720x480 or 640x480

To get it to work I did the following:
1) Use Powerstrip on a Vista box to get the modeline for 1280x720 for the monitor
2) Used the following commands in a Linux terminal to get it to work:

xrandr --newmode blah blah blah
xrandr --addmode HDMI1 blah blah blah
xradnr --output HDMI1 blah blah blah

This works great! However whenever I restart Mythbuntu I end up back in 720x480.

How can I get the box to start up in 1280x720 mode?

I tried hacking the /etc/X11/xorg.conf file. This file did not exist initially. I used "Xorg -configure" to create one. I've tried mucking about in the xorg.conf file but nothing seems to get me into 1280x720 mode.

Is there a way to tell Mythbuntu to start up in 1280x720 mode? Do I have to put the xrandr commands in a start up script somewhere to make this happen?

Thanks for any help

---

