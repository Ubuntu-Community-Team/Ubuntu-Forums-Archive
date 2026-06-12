---
title: "Fiesty upgrade broke my X"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Mantis2600 on 2007-04-25
Hello,

After I restarted from the upgrade, x failed to start.  I have no idea what to do to try to fix it.  Running an Nvidia 6800 and had working Twinvision.  I can't do a lot of pasting configs as I'm on a pda as a last resort.  Any help is appreciated.

---

### Post by dfreer on 2007-04-25
sudo dpkg -reconfigure xorg-xserver

Or, if you would like to keep your /etx/X11/xorg.conf file, just edit it and change the video driver from nvidia to nv. Then you will be able to at least post from your PC.

---

### Post by Mantis2600 on 2007-04-25
that command didn't work...

dpkg:conflicting actions -e and -r

---

### Post by sisco311 on 2007-04-25
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dfreer on 2007-04-25
oops! completely messed that command up :( that's what I get for doing it from memory

---

### Post by Mantis2600 on 2007-04-25
Allright, an update...I reconfigured the Xserv and got the following problem (I should note changing the driver to nv instead of the nvidia driver resulted in the same problem):


X "loads"  but the screen remains black and I hear the ubuntu drums.  If I try to login by typing username and password, I can login as the sounds play, but the screen fills with garbage and is completely unintelligible.  It's also worth noting if I try to login and get garbage killing x and trying to go to terminal fails because the terminal screen still outputs garbage and artifacts.

---

### Post by sisco311 on 2007-04-25
[try out this]("http://ubuntuforums.org/showthread.php?t=422918")

---

### Post by Mantis2600 on 2007-04-25
I'm unable to try that because my screen (terminal included) is full of garbage and artifacts making it impossible to read anything.  I'm going to try to mess with my config to address this, but any help would be awesome as I'm a bit of a newbie.

---

### Post by Mantis2600 on 2007-04-25
update: I'm able to follow that guide now.  I was able to trash my xconf.org file but following commands from memory forcing myself into a failure of the Xserv allowing me to get to a clean console, but when I reconfigured the Xserv it did the exact same thing.  Also I was able to follow the guide up to installing the driver, but what command do I need to use to install the nvidia driver(s)?

---

### Post by Mantis2600 on 2007-04-26
> **sisco311 said:**
> [try out this]("http://ubuntuforums.org/showthread.php?t=422918")

This worked...now I just need to tweak twinview so that my windows don't maximize across the screen.

---

### Post by JustinJS on 2007-04-26
Thank god i found this i have been trying to get it to work for 3 days lol

---

### Post by RAKninja on 2007-04-26
I'm still having no luck, i think my intel integrated gfx is trying to force itself as default and theres not anything i can do about it =\

---

