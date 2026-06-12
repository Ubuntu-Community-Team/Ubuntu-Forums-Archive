---
title: "Disable external VGA port on boot"
date: 2010-06-06
forum: Multimedia Software
---

### Post by pawaman on 2010-06-06
Hello everyone, and I'm sorry for my bad English

I have an hp pavilion zv 6000 with ATI RADEON XPRESS 200M video card, and kubuntu x64 as operating system.
For some time now I can connect a second screen (1024x768 ) to the laptop (with 1280x800 max resolution) .
If I turn on the PC with the VGA port connected it clones the output by changing the resolution of both displays to 1024x768, forcing me to change video settings each time i log in for bring the situation to normal.
Instead I wish to keep disabled the external screen during boot and go to these settings when I need to use it. Now I am forced to start the PC with the VGA port physically disconnected and attack it after the boot is finished.

Is possible to fix things?
Thank you!

---

### Post by gordintoronto on 2010-06-06
Have you looked in the computer manual? I think this is a hardware question.

---

### Post by pawaman on 2010-06-12
I have tried to access to windows 7 and the behavior is the same on boot. The output is cloned. Then I think that gordintoronto have right about the hardware feature. I have checked inside BIOS and I found nothing.

But when I access to win7 login screen and then to desktop the resolution is keep from the previous session.

making reference to:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login")

I have set up a /etc/X11/Xsession.d/45custom_xrandr-settings file with the following code:

```
xrandr --output LVDS --auto --output VGA-0 --off
```

At this point, after login the main screen resolution is correct and the second screen is disabled. Exactly what I want to do.

The problem of login screen with cloned low resolution still remain

I have changed topic seeing that I think is not a boot problem

---

