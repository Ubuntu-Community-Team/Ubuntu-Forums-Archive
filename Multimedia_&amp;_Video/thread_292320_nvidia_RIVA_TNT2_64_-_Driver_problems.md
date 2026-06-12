---
title: "nvidia RIVA TNT2 64 - Driver problems"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by lemonsCC on 2006-11-03
I am trying to install the drivers for my nvidia RIVA TNT2 64 video card, but not having any luck.  I tried following this guide but it didn't work.  [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

Please help

---

### Post by tseliot on 2006-11-03
you have to use the legacy driver.

Which method did you use?

---

### Post by lemonsCC on 2006-11-03
used the legacy drivers and method 1

it isnt really imporant.  I just wanted non-emulating google earth....

---

### Post by tseliot on 2006-11-04
> **lemonsCC said:**
> used the legacy drivers and method 1

it isnt really imporant.  I just wanted non-emulating google earth....

post the output of this command:
```
glxinfo | grep direct
```

---

### Post by jbtito03 on 2006-11-04
Mine is :

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Please help...

---

### Post by metcalfe on 2006-11-04
i have the same graphics board and the same problem!

i created a topic [here]("http://ubuntuforums.org/showthread.php?p=1711423#post1711423") where i discuss what i did (yet still have no success), but you should maybe try to replace "nv" for "nvidia" in your device section of /etc/X11/xorg.conf, if you haven't got that already.

anybody have any ideas to solve this?

---

### Post by tseliot on 2006-11-04
I think you should start a new thread here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

the Nvidia staff will help you there.

---

### Post by lemonsCC on 2006-11-04
The computer has been passed off.  Google earth is slow, but the user is a non-computer literate older gentleman.  He wanted it to just work, and is overly thrilled with the end product (and cost) of Ubuntu.

---

### Post by owyn on 2006-11-11
I have the same card and the Ubuntu 6.10 support is definitely brain dead, if not broken.

Setting up a new multi-boot Linux test system. The system I am using has a MSI KM400 integrated motherboard. There seemed to be problems with getting it's integrated audio and video working with various Linii so I installed known working SB Live and Riva TNT2 M64 cards.

I had planned to set up this system using Ubuntu 6.10 desktop. However, the CD only supports 800x600 and 640x480 in gdm for this card. The install dialog was not usable at 800x600. 

I switched tactics and used a PCLinux OS 0.93a Big Brother Live CD to prep the system and installed PCLos as the base OS. It supports the Riva perfectly.

I found out about ALT left drag this morning, so I actually was able to use the Ubuntu installer today (my other plan was to use an alternate CD). Hoped that the xres problem would be fixed after the install to hard disk. No such luck. The card is properly identified but the config is totally inappropriate. Not fubar, I am sending this message from Ubuntu.

Anyway, off to test a cut and paste from PCLos to Ubuntu. I do have a working xorg config on hda1. Time to promote it to this partition. :twisted:

---

### Post by owyn on 2006-11-19
Finally found the fix.

Needed to add

```

HorizSync 30-69
VertRefresh 50-120

```

to Section "Monitor" in xorg.conf

These settings are correct for my monitor. Others would have to check specs for their monitor.

---

