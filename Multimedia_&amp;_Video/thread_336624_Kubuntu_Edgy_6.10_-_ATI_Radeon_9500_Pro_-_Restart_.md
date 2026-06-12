---
title: "Kubuntu Edgy 6.10 - ATI Radeon 9500 Pro - Restart after logging in"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by JarrettBillingsley on 2007-01-11
I've installed Kubuntu Edgy, and I'm trying to get my graphics drivers installed properly.  I've followed both methods on the BinaryDriverHowTo/ATI Wiki page, as well as several other methods listed in various threads.  

No matter how I install the fglrx drivers, the same thing happens:

Kubuntu starts up.  The login screen appears, in 1600x1200 resolution, so it seems like the drivers are working properly (the default drivers start up in 800x600).  I log in.  After about three seconds, before the loading screen appears, X seems to restart, like hitting ctrl+alt+backspace.  I am back at the login screen.

I can do this all day.  It never successfully logs in.

I've looked at /var/log/Xorg.0.log and /var/log/syslog; neither have anything revealing.  The Xorg log has the typical Wacom errors, and one error regarding AIGLX not being able to call __driCreateDisplay or something like that because it couldn't dynamically link it, and so it reverts to software rendering.  But there's no major error, and that AIGLX error isn't even the last error in the file, so it's not like the system restarts right then either.

I've tried different driver versions, I've tried reinstalling Kubuntu, I've tried every method of installing the drivers.  I am at my wit's end over something that I would think should be a very simple and mundane task.

Please tell me what you need -- logs, specs, whatever -- and I'll be glad to post.

---

