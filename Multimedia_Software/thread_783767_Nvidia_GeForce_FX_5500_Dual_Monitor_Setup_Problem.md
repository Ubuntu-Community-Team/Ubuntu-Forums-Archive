---
title: "Nvidia GeForce FX 5500 Dual Monitor Setup Problem"
date: 2008-05-06
forum: Multimedia Software
---

### Post by neogeek on 2008-05-06
Hi,

I have an Nvidia GeForce FX 5500 graphics card. I finally managed to get the drivers installed properly.

I have a dual monitor setup but I cannot seems to get the secondary monitor to work.

I went to the Nvidia X Server Settings and my second monitor is recognised but disabled.

Everytime I enable it and restart and apply, it just go back to the original setting of being disabled.

I aslo tried the Save X to configuration file option and this is the error I get:

[COLOR="Blue"]Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.[/COLOR]

Would appreciate any help. :confused:

Thanks!

---

### Post by Seks on 2008-05-06
use sudo or do it as root.

Also, would you mind posting your xorg.conf and telling me what you did/what driver? I have the same card but I can't get it to work :(

---

### Post by neogeek on 2008-05-07
Tried sudo in the terminal window - still didn't work.

I used the Synaptic Package Manager and installed the nvidia-glx-new package and the nvidia settings.

I am using the Ubuntu 8.04 version.

If you still need the xorg.conf let me know, I will post.

Thanks!

> **Seks said:**
> use sudo or do it as root.

Also, would you mind posting your xorg.conf and telling me what you did/what driver? I have the same card but I can't get it to work :(

---

### Post by neogeek on 2008-05-07
I finally got my dual monitors to work with the Nvidia GeForce FX 5500.

Here is what I did -

- Installed the nvidia-glx-new package and the nvidia settings using the Synaptic Package Manager
- Opened up terminal and typed in sudo /usr/bin/nvidia-settings
- Applied the X screen for both.
- Restarted the computer.

It also solved the problem of the login screen being cut off - I guess it was set to a lower resolution.

Hope this helps.

---

### Post by mulcyber on 2008-08-04
Hi, I have the same card and tried to set up Kubuntu 8.04.1
Well, I first only got one monitor to work. Also it revoked
Windows XP successful usage of both monitors. The solution 
I found which is more detailed and comes with a video is at

[http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/](http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/)

---

### Post by QIII on 2013-02-18
Old thread.

New responses moved to own thread.

*Thread **closed.***

---

