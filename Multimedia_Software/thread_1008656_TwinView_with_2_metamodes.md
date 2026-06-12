---
title: "TwinView with 2 metamodes"
date: 2008-12-11
forum: Multimedia Software
---

### Post by Stuart Coyle on 2008-12-11
I have managed to get Twinview working with my trusty old Nvidia card and it is very nice when it does work. It works fine when I have only one metamode or have only metamodes listed that use both monitors in xorg.conf. 

But...if I do something like this in the Screen section of xorg.conf:
 ```
   
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBVisuals" "true"
    Option         "AddARGBGLXVisuals" "true"
    # Option         "AllowGLXWithComposite" "1"
    Option         "SecondMonitorHorizSync" "30.0 - 70.0"
    Option         "SecondMonitorVertRefresh" "50.0 - 160.0"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1024x768 +1280+0; CRT-0: 1280x1024 +0+0, CRT-1: NULL"

```

Notice that the second meta mode only has one monitor. I use this for games that don't work well across two screens as well as for If I want to use the second monitor output for a projector that I can turn on and off.

What happens is that on startup is this: At the Ubuntu login prompt I'm in the first metamode with both screens working fine, then when I log in it switches to the single screen mode. Most annoying. Even more annoying is that I cannot ALT-CTRL + or - to change modes.

I have this odd line in /var/log/Xorg.0.log:
```
AUDIT: Fri Dec 12 09:09:32 2008: 8230 X: client 2 rejected from local host (uid 1000)
```
What's that about?

Once logged in I can change back to the first metamode by using ```
xrandr -s 0 
``` and then ALT CTRL +/- works again...sometimes.

I'm usually fine at working out Xorg issues but this one has me stumped. What is Ubuntu doing on login? I have nothing in .profile that should affect screen resolution. Is it something to do with Gnome setting the background? 

Any clues?

---

