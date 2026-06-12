---
title: "Refresh Rate Stuck at 75Hz"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by smsader on 2006-11-03
I am more or less new to Linux and just installed Ubuntu 6.10.  I have a Dell 2007FP monitor that is supposed to run at 1600x1200 at 60Hz, and it has been hell from the start.  First of all, the initial install process wouldn't let me see anything on the display.  I ended up "tricking" it by unplugging my monitor at the beginning of the install process and then plugging it in.  That set me up to the default of 1024x768.

Next, I tried running dpkg-reconfigure -phigh xserver-xorg.  From there, I was able to select resolutions of 1600x1200 and 1280x1024.  However, the 1600x1200 failed to display anything on my computer.  So I ran the command again and this time selected only 1280x1024.  The 1280x1024 does work on my display.  However, when I go into the System Preferences to view the resolution and refresh rate, the refresh rate is stuck at 75Hz with no option to change it.  I figure that is what is preventing me from displaying at 1600x1200, because it needs to be at 60Hz yet is stuck at 75Hz.  Can anyone help me get my monitor set and working properly at 1600x1200@60Hz?  Thanks so much for the help! Scott

---

### Post by John.Michael.Kane on 2006-11-03
This thread maybe of some use [http://ubuntuforums.org/showthread.php?t=289269&highlight=xorg](http://ubuntuforums.org/showthread.php?t=289269&highlight=xorg)

---

### Post by smsader on 2006-11-06
I've tried everything in the thread you recommended I look at, and I still am stuck at 75Hz!  When I try to add the "_60" to the xorg file i.e. "1280x1024_60," it seems to skip that resolution all together and not allow me to display at that resolution at all.  Any more ideas?

---

### Post by smsader on 2006-11-13
Thanks to those of you who took the time to read this thread.  I guess I'm going to have to scrap Ubuntu for another distribution that won't cripple my resolution.

---

### Post by justinjstark on 2006-11-13
Before you go, open up your monitor onscreen prefs and make sure it is actually at 75hz.  Gnome says my display is at 50 something hz but really it's at 75 if I check it on my on-screen monitor displays.

---

