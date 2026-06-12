---
title: "nvidia-settings not saving changes after closing some 3d programs"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by Waste on 2006-07-30
Hello, I am having a few issues with nvidia-settings not restoring it's settings after runing certain 3d programs.
The ones that it does this on that I can remember off the top of my head if any gnome screensaver, a couple of games (I think Warsow is one, specifically.), and for some reason amarok makes it reset as well.

Is there any possible way for me to stop it from doing this altogether, or is there a way I can have it automatically apply the settings after I close a 3d program instead of me having to do it manually?



[edit]
Also, where exactly is the config file for nvidia-settings?
I'd like to manually change some things within this file if it's possible.

---

### Post by tseliot on 2006-07-31
Get to the following menus (if you use GNOME):
System -> Preferences -> Sessions -> Startup Programs

Then click on "Add"

And insert this command:
```
nvidia-settings --load-config-only
```

Then click on "Close".

---

### Post by Waste on 2006-07-31
I've already added that.
It does nothing.
I've tried both methods that I have seen on the forums and neither of them apply the settings at startup.
Nothing fixes them resetting after the 3d programs are run either.

---

### Post by tseliot on 2006-07-31
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

