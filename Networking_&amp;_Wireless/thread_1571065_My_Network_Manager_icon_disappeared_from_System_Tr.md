---
title: "My Network Manager icon disappeared from System Tray"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2010-09-09
I am not sure where is my network manager. Every time I write nm-applet, I get the following error:


```
$ nm-applet 
An instance of nm-applet is already running.

** (nm-applet:3526): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

---

### Post by DjSesso on 2010-09-09
> **OOzypal said:**
> I am not sure where is my network manager. Every time I write nm-applet, I get the following error:


```
$ nm-applet 
An instance of nm-applet is already running.

** (nm-applet:3526): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

should be able to right click on the panel at the bottom then panel options, then add widgets. In there look for the NM. :)

---

### Post by FuFu Tantrum on 2010-10-06
I'm having the same problem. Actually I was going to just move it, I can't remember why, and I accidentally REmoved it from my panel. Since then I haven't been able to get it back. I've tried killing the network manager and restarting it, I've tried running the nm-applet --sm-disable, running it without --sm-disable just in case that had something to do with it, tried reinstalling it, tried to see anything in the .desktop file... I've exhausted my limited resources. I'm rather new to Linux and I just can't figure this out.

---

### Post by dineshs on 2010-10-06
Right click on the top panel-click add to panel-select notification area -click add
If the icon is still not visible please post the contents of /etc/network/interfaces```
gksudo gedit /etc/network/interfaces
```

---

### Post by FuFu Tantrum on 2010-10-07
Thanks! I actually was able to talk with one of my coworkers and get it sorted out. I just spent all my time looking in there for network manager. I had no idea about this "notification area" thing. Now I do. I guess that's how you learn. Again, thanks.

---

### Post by agnivade on 2010-11-18
Hey, I am having the same problem too. Though I have absolutely no idea how it happened. Just all of a sudden.

I have tried nm-applet(It shows that nm-applet is already running), nm-applet --sm-diable

Also right clicking on taskbar, add to panels, clicking notification area doesn't help too. Its already there. I know this works, but not working for me.

PLz help anybody.

---

### Post by czege on 2010-11-18
Here's the thread where I asked for help for the same thing. The solution that worked for me was posted by dineshs:

[http://ubuntuforums.org/showthread.php?t=1621690](http://ubuntuforums.org/showthread.php?t=1621690)

Paul

---

### Post by agnivade on 2010-11-20
Hey thanks, dineshs solution worked. But now, there is a red exclamation sign saying that wireless networks are disabled

Help needed again !!

---

### Post by gauchoproluanco on 2011-03-14
It works!

Thanks a lot Dinesh!!!

Luis

---

