---
title: "sometimes xinearama, sometimes single head part 2"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by mvsjes2 on 2007-04-13
Continuing on the journey of X lameness from this thread:
[http://ubuntuforums.org/showthread.php?t=404310](http://ubuntuforums.org/showthread.php?t=404310)

I have my script working so that I get the correct xorg.conf file copied in when I have either my dell monitor, my toshiba tv, or both plugged in.

I now have a problem with the toshiba.

When I have my Dell plugged in and the toshiba becomes the second monitor, everything's fine on the tv, I get a 1280x720_60 signal and the font size is normal.

When I unplug my Dell and reboot, and the Toshiba becomes the only display, the fonts become huge, so big that it's almost unusable. For example, if I right click on the desktop the menu almost fills the whole screen. It's behaving as if it's getting a 640x480 or 800x600 signal from the video card. The font size according to systemsettings is the same: 12. I have to reduce them to 8 in order to be able to function.

If I check xorg.0.log or start nvidia-settings, they both tell me the same thing, that the tv is still using the same resolution as when the dell is plugged in: 1280x720.  xorg.0.log confirms that "1280x720_60"  is validated and is accepted. Something's not right though.

Can anyone enlighten me as to what's going on? I'm using edgy with an nvidia geforce 6200. The monitor is in the vga port and the tv is using a dvi-hdmi cable.

<rant>I simply can't get over how lame X is. It has to be dragged kicking and screaming into the 1990s. All I want to do is set up my monitors so that I can plug in the one I want to use and have the system use my defined settings for them. You'd think this would not be too difficult to do, but I have literally spent a week and a half on this and it's still not working. The solution I have come up with so far is (see link above) a pretty lame workaround. The software is simply too rigid and inflexible for these enlightened times. Sorry, it's been a long week.</rant>

---

### Post by mvsjes2 on 2007-04-13
Oh yeah, I'm on 9746 nvidia driver level.

---

### Post by mvsjes2 on 2007-04-14
It turned out to be a DPI issue. For some reason it was using different values depending on whether or not the monitor was plugged in. I forced it to 100x100 and all is well.

Now I just have to figure out a modeline to fix huge overscan and I'll be all set.

---

