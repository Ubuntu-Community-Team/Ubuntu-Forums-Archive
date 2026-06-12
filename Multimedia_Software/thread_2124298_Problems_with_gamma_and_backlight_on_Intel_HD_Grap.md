---
title: "Problems with gamma and backlight on Intel HD Graphics"
date: 2013-03-10
forum: Multimedia Software
---

### Post by deviskec on 2013-03-10
I have a problem keeping my settings for gamma and backlight on an Ubuntu 12.10 64-bit version. I can successfully set the values using the xgamma and xbacklight programs, however this settings get reset on restart. So I added a startup script which works, however whenever I switch to AC power or plugin HDMI the settings get reset. I tried using a loop/timer, but since setting this settings is quite an expensive operation, the entire UI blocks whenever I set them which is quite annoying. Even using an IF statement doesn't help, because even though the gamma and backlight change, the xgamma and xbacklight programs aren't aware of it and still report old values. I don't have a xorg.conf file and generating one fails, os I can't set the default values in there. My question would be, who is changing these values when display settings change (lightdm, acpi or something), and where can I SPECIFY DEFAULT GAMMA AND BACKLIGHT VALUES for those programs to use?

---

