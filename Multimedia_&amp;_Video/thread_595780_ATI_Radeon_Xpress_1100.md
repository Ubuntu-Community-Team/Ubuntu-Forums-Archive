---
title: "ATI Radeon Xpress 1100"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by DBAlex on 2007-10-29
Hi,

I installed the restricted driver in Add/Remove programs for ATI Cards but I still can't enable desktop effects?

Why is this? I can get a full 1280x800 laptop display and the card is recognized from a **lspci** command...

Thanks for any help.

---

### Post by DBAlex on 2007-10-29
ARGH!!! 

WHY DO I NOT RECEIVE ANY HELP ON THIS FORUM...

IVE POSTED 3 TOPICS AND GOT NO HELP ON ANY OF THEM

:mad: :mad: :mad: :mad:

---

### Post by DBAlex on 2007-10-29
Anyone?

:(

---

### Post by jpittack on 2007-10-29
Yo.

Tell me what your output for fglrxinfo is.  I have the same graphics card and have everything working.  Lets get everything working for you.

Make sure you add compiz config settings manager from the package manager.  Without it you won't get far.

Don't forget to tell me fglrxinfo and then we can get started on getting you eyecandy.

---

### Post by DBAlex on 2007-10-29
jpittack,

Ok thanks for your help, heres the output of fglrxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

And I installed the Compiz Manager from Synaptic too...! :)

Hope you can help me with that info... IIRC when I used Ubuntu a long time ago Vesa means the driver isn't installed properly?

Thanks, Alex.

---

### Post by jpittack on 2007-10-29
Mesa is bad.  Driver is not installed properly.  

What version of Ubuntu and architecture are you using (32 or 64 bit)?

Have you messed with your driver at all before this?

---

### Post by DBAlex on 2007-10-29
Hi,

Yeah im using Ubuntu 7.10 32-Bit...

And yes I have messed with the driver a bit, I installed first a proprietary driver for 200M chipsets (Same chipset according to wikipedia) from ATI's website, when installing this though once I had reconfigured my XServer I just got a white screen on startup, so I reconfigured the XServer to use VESA to get the nice 1280x800 display I had back...

I then installed the X.org ATI Driver from Synaptic/Add-Remove Programs... I seem to be in a bit of a mess though...

Where should I go from now? Oh and I did un-install the driver from ATI's website before installing the new driver...!

Hope you can give me some pointers on where to go from now! :)

Thanks, Alex.

---

### Post by jpittack on 2007-10-29
Here is my first suggested thread.

[http://ubuntuforums.org/showthread.php?t=592805&highlight=ATI]("http://ubuntuforums.org/showthread.php?t=592805&highlight=ATI")

I was able to get my driver installed via a clean install and using restricted drivers manager.  I am in 64 bit, so I have trouble with the how tos because the installer for 64 bit is broken.  You may not need a reinstall.

Future reference.  Back up /etc/X11/xorg.conf
Something goes wrong, overwrite the bad one.  Don't back up the one that you have now.

Following an attempt to install the driver, could I get the output of
>  sudo gedit /etc/X11/xorg.conf  
I don't really know what I'm doing (I'm sure this is comforting), but mabye I will see something.  Only give this to me if nothing works.

---

### Post by DBAlex on 2007-10-30
The article linked to in the article you posted was very useful!

everything is working fine now, I have set up OSX Leopard like spaces set to the F11 key!

Very very nice! :) (I can drag a window from one space to the next!)

Much more exciting than plain old XP anyway...! 

Thanks by the way, one think I found is that firefox scrolling is quite slow now, I read in another post though than it isn't in opera, so I might start using that, anyway thanks for the help!

:) :) :) :)

---

### Post by jpittack on 2007-10-31
2D is much slower with this new driver.  I do not have the issues in firefox all the time, but they do show up.  One 2D game that I commonly play has scrolling issues.  I ignore them and focus on my battle strategy (Battle for Wesnoth).

If you really want a great experience with Ubuntu, customizing the desktop is a great (sometimes frustrating) experience.  Sounds like you already got around to it.  PM if you have a new thread.

---

