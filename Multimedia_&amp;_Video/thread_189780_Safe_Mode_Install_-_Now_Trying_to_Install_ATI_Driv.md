---
title: "Safe Mode Install - Now Trying to Install ATI Drivers"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by OneL on 2006-06-05
I've been working with Windows for years but know only enough about Linux and Ubuntu to be dangerous.  Here's the problem:  I had a problem installing Dapper and found that I could do it in safe mode.  I'm up and running now, but I want to change my vesa video driver to the ati driver so that I can run my Dell 2005FPW monitor in native resolution (1680x1050), something that the vesa driver doesn't permit.  I've read and followed the unoffical ATI wiki and several posts in the forum concerning installing ATI drivers but nothing seems to work.  Yes, I know that posting the error messages would be helpful, but I figured that if I just plow on I would get something to work, so I didn't record them.

I can't successfully download another driver via apt-get.  I see that the linux-restricted package which contains the fglrx driver was installed but I do not know what to do to get that driver installed.

My system has a Gigabyte x800xl card and I am running a dual boot with XP.  Any help from out there would be appreciated.

---

### Post by BaffledMollusc on 2006-06-05
[QUOTE=OneL]I've been working with Windows for years but know only enough about Linux and Ubuntu to be dangerous.  Here's the problem:  I had a problem installing Dapper and found that I could do it in safe mode.  I'm up and running now, but I want to change my vesa video driver to the ati driver so that I can run my Dell 2005FPW monitor in native resolution (1680x1050), something that the vesa driver doesn't permit.  I've read and followed the unoffical ATI wiki and several posts in the forum concerning installing ATI drivers but nothing seems to work.  Yes, I know that posting the error messages would be helpful, but I figured that if I just plow on I would get something to work, so I didn't record them.

I can't successfully download another driver via apt-get.  I see that the linux-restricted package which contains the fglrx driver was installed but I do not know what to do to get that driver installed.

My system has a Gigabyte x800xl card and I am running a dual boot with XP.  Any help from out there would be appreciated.[/QUOTE]
All I needed to do to install a working fglrx driver was to install the fglrx package using Synaptic, and then type "sudo aticonfig --initial" in a terminal to fix up my xorg.conf file.

Of course, the fglrx driver seems to have a number of bugs, but that's another story...

---

### Post by OneL on 2006-06-06
After reading the issues that are out there with XServer and the ATI drivers, I've removed Ubuntu.  I'll wait for these issues to sort out, and then I'll try again.

---

### Post by -::Bas::- on 2006-06-23
Try this: [http://www.ubuntuforums.org/showthread.php?t=200559](http://www.ubuntuforums.org/showthread.php?t=200559)
Remove Windosw, that's much safer ;)

---

