---
title: "Ubuntu Gnome 14.04 forgets multi-monitor settings"
date: 2014-04-19
forum: Multimedia Software
---

### Post by The Bright Side on 2014-04-19
Hello fellow Ubuntu fans!

I installed the new Ubuntu today and have spent the past few hours struggling with a problem I thought had been resolved long ago.

I have a monitor hooked up to my NVidia card's DVI output, and a 5.1 sound receiver to the same card's HDMI. Now, since HDMI transports both video and sound, Ubuntu thinks the receiver is another monitor and automatically places it next to my actual screen.

So every time I move the mouse to the right edge of my screen, it disappears onto the invisible second screen. To fix this, in the past, I just moved the screen settings so they only touch each other in one corner. However, Ubuntu 14.04 doesn't remember my preferences. Nor does nvidia-settings.

Every time I reboot, I have to set this up again.

I know this is a well-documented and well-known problem, but all the threads I went through didn't have an easy solution for me. I tried this with Nouveau and the latest NVidia driver (331), and I tried deleting and rebuilding the xorg.conf and monitors.xml files. I even set them both to read-only. It seems like Ubuntu just completely ignores them: every time I reboot, the monitors are back to the setting I don't want.

In addition, this funny thing happens:

When I turn the receiver off and back on, then sometimes (in about 1 out of 5 cases), the constellation is actually correct!

Any ideas would be highly appreciated. It's driving me crazy. This was perfectly fine in 13.04 and 13.10... I set the "monitors" up once and all was good. :-/

---

### Post by Steven_Eardley on 2014-04-26
See [this question]("http://askubuntu.com/questions/450767/multi-display-issue-with-ubuntu-gnome-14-04") - it's a known bug with a simple workaround: 

[FONT=Ubuntu Mono]pkill -9 -f gnome-settings-daemon
[/FONT]
Works any time, or you can add it to run at boot.[FONT=Ubuntu Mono]


[/FONT]

---

