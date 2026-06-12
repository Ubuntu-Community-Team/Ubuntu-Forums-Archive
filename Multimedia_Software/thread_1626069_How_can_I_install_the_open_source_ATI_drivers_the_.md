---
title: "How can I install the open source ATI drivers the right way?"
date: 2010-11-19
forum: Multimedia Software
---

### Post by travlemon on 2010-11-19
Hello everybody,

I am trying to install an ATI Radeon 9550 256mb AGP card in Ubuntu.  When I first installed Ubuntu, the card appeared to work out of the box, but it seemed like it was struggling in certain 3D games that it shouldn't have.  I have a dual boot setup, and in Windows XP, it runs pretty graphically impressive games (from 2003 or 2004) without a problem.  However in Ubuntu, it has problems even with certain 2D games and things like SuperTuxKart, which seem not nearly as straining on the card as the things I tested in Windows.

So, I tried to install the proprietary ATI drivers, and received an error.  I found a fix online and it helped me install the driver.  Here is the fix: [http://ubuntuforums.org/showthread.php?t=1221221](http://ubuntuforums.org/showthread.php?t=1221221)

It seemed to improve the issue a little bit, but I think I might just be looking to hard and nothing improved at all.  Either way, the issue didn't go away. I then decided to try to install the open source ATI drivers, and this is where I have more problems.   I found a guide on the Ubuntu site and it didn't seem very clear to me, and I don't know what the status of the card is, or which driver is really installed now.

The certain things seem to run ok, and smoothly, I can tell that the card is somewhat active.  Docky looks great, and a couple non-opengl games.  But now, nothing with opengl works.  I ran glxinfo and get this error:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat

I ran glxgears and get this error:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


Can someone help me to try to make sense of what's going on, and maybe help me to install the open source ATI drivers the right way?  Here is a link to the tutorial that I tried to follow, and I also tried following the included link to setup KMS, but I kept getting an error when trying to modprobe radeon:  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks in advance! I'm stuck!

---

### Post by travlemon on 2010-12-02
> **travlemon said:**
> Hello everybody,

I am trying to install an ATI Radeon 9550 256mb AGP card in Ubuntu.  When I first installed Ubuntu, the card appeared to work out of the box, but it seemed like it was struggling in certain 3D games that it shouldn't have.  I have a dual boot setup, and in Windows XP, it runs pretty graphically impressive games (from 2003 or 2004) without a problem.  However in Ubuntu, it has problems even with certain 2D games and things like SuperTuxKart, which seem not nearly as straining on the card as the things I tested in Windows.

So, I tried to install the proprietary ATI drivers, and received an error.  I found a fix online and it helped me install the driver.  Here is the fix: [http://ubuntuforums.org/showthread.php?t=1221221](http://ubuntuforums.org/showthread.php?t=1221221)

It seemed to improve the issue a little bit, but I think I might just be looking to hard and nothing improved at all.  Either way, the issue didn't go away. I then decided to try to install the open source ATI drivers, and this is where I have more problems.   I found a guide on the Ubuntu site and it didn't seem very clear to me, and I don't know what the status of the card is, or which driver is really installed now.

The certain things seem to run ok, and smoothly, I can tell that the card is somewhat active.  Docky looks great, and a couple non-opengl games.  But now, nothing with opengl works.  I ran glxinfo and get this error:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat

I ran glxgears and get this error:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


Can someone help me to try to make sense of what's going on, and maybe help me to install the open source ATI drivers the right way?  Here is a link to the tutorial that I tried to follow, and I also tried following the included link to setup KMS, but I kept getting an error when trying to modprobe radeon:  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks in advance! I'm stuck!

To follow up on this topic and get it out of the way, I think the drivers were already installed when I installed Ubuntu.  As for the poor performance, this may just be another reason why I've always liked Nvidia better.  I've always had glitchy issues with ATI cards, and never anything like that with Nvidia cards.  That is, of course, with the exception of the Geforce2 Go MX440 mobile graphics installed in a Toshiba Satellite Pro 6100.  That is probably the most troublesome graphics/laptop combination ever created!

Anyway, I think the answer to this thread is that Ubuntu installs the drivers automatically, but if not, install the fglrx package in Synaptic to get the open source driver installed.

---

### Post by Yellow Pasque on 2010-12-02
> **travlemon said:**
>  I think the answer to this thread is that Ubuntu installs the drivers automatically
Correct. 

> but if not, install the fglrx package in Synaptic to get the open source driver installed.
No. fglrx is the proprietary driver and it doesn't support non-RadeonHD cards. If you want a newer open-source driver, see:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by travlemon on 2010-12-02
> **Temüjin said:**
> Correct. 


No. fglrx is the proprietary driver and it doesn't support non-RadeonHD cards. If you want a newer open-source driver, see:  [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

thanks for the clarification, i'm all out of wack with these drivers haha.  is the xserver-xorg-video-ati package the one that i want? i'm very unfamiliar with installing video drivers other than official Nvidia .run files.  would the correct order be to uninstall the fglrx package and install the xserver-xorg-video-ati package?

thanks in advance

---

