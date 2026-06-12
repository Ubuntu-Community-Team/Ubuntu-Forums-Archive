---
title: "More Dual Head Woes"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by nahgoe on 2008-01-18
I've searched the forums and tried various answers, but none of them have quite worked. I have an ATI X1300 card, with two monitors (a Dell 20" Widescreen and a 19" 4:3 monitor). I have fglrx working properly, however I can't make the two monitors display different resolutions.

I've tried various aticonfig commands to set pairmodes, and to try force resolutions on the monitors, but they both display at 1280x1024 (the 20" should be able to do 1680x1050). Anyone know how to make it work properly?

Thanks!

---

### Post by perixx on 2008-01-18
Hi nahgoe.

I can't promise any success for you... but here's a step-by-step Howto on how to use XINERAMA and set up dualscreen in xorg.conf:
[http://ubuntuforums.org/showthread.php?p=1773624]("http://ubuntuforums.org/showthread.php?p=1773624")

FIRST, you should really back up your old /etc/X11/xorg.conf, though, if you haven't done so yet:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` Then you can always revert to it on the command line, should you not be able to get into desktop anymore.

I've read some issues about your specific widescreen resolution not working on some pieces of hardware and/or drivers and I don't know your card, so...

But what driver version do you have? You might try to use another (newer) driver perhaps. If you got a newer version than 8.35.xx you should have 'amdcccle' installed with the driver, which gives you the possibility to set dualscreen resolutions via GUI (if it's working). So I'd recommend to try that first...

Here you can find a small pack of links that might be useful to you if you have trouble with the ATI driver...
[http://ubuntuforums.org/showpost.php?p=4127616&postcount=26]("http://ubuntuforums.org/showpost.php?p=4127616&postcount=26")

perixx

---

