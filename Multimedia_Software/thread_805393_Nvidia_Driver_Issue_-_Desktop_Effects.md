---
title: "Nvidia Driver Issue - Desktop Effects"
date: 2008-05-23
forum: Multimedia Software
---

### Post by bung33 on 2008-05-23
I've done this a million times on other computers with earlier versions and never had any problems, but for some reason, I can't get this to work...

I wanted to enable the desktop effects, so I let Ubuntu download and install the proprietary Nvidia driver. After restarting X, my screen looks like a modern art painting -- a bunch of black, white, and colored lines. I switched to a different TTY and reset my settings. Then I installed EnvyNG, figured it couldn't hurt since it was updated for Hardy. Long story short, same thing -- lots of lines. I've got a Dell XPS M1530...

At this point, I don't even care about the desktop effects -- I just want to get the video card working right. Any suggestions?

---

### Post by bung33 on 2008-05-23
In the mean time, I tried downloading the latest version from Nvidia, which was the same version EnvyNG tried to install, but whatever. Anyway, downloaded, recompiled the kernel interface, installed, blah, blah, blah... more lines. No solution...

---

### Post by bung33 on 2008-05-24
Forgive the waste of space. Problem solved with the latest Nvidia beta driver...

[http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html](http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html)

---

### Post by volgotron on 2008-06-08
> **bung33 said:**
> Forgive the waste of space. Problem solved with the latest Nvidia beta driver...

[http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html](http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html)


Not really completely solved....Googling on the Net, I knew of many people trying to configure XPS M1530 with no results.......Here I found the right way to do it! I've been working around it for 2 months with no way to get it (after rebooting my X11 settings disappeared) but now, following this guide, everything is ok!!!It's in Italian but just follow the cmds and everything will be ok.....
This is the link [http://mbutiesubbaqqui.blogspot.com/2008/05/nvidia-8600-non-funzionante-su-hardy.html]("http://mbutiesubbaqqui.blogspot.com/2008/05/nvidia-8600-non-funzionante-su-hardy.html")

---

