---
title: "Is it possible to force 1920x1080 over HDMI?"
date: 2008-10-10
forum: Mythbuntu
---

### Post by Caps18 on 2008-10-10
I currently use a powered HDMI splitter to have the signal go to a LCD TV and projector.  Both use 1920x1080, and the splitter can handle sending that resolution to both of them.  The problem comes when I restart my Mythbuntu box, it thinks it is connected to a 1280x1024 monitor if they are plugged into the splitter.  If I have it plugged in directly to the LCD TV, it chooses the correct 1920x1080.

---

### Post by SiHa on 2008-10-10
Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Yours is similar to the problem I had in this thread:

[http://ubuntuforums.org/showthread.php?t=913224](http://ubuntuforums.org/showthread.php?t=913224)

Where it would set the wrong resolution if it couldn't autodetect the device, The above guide helped me fix it.

Essentially, you need to remove all resolutions apart from the required on in xorg.conf, and tell the PC to ignore the fact that it can't get any information via EDID.

You will probably need to add a modeline in there, so that the card knows how to drive at 1920x1080 when it can't get EDID info.

**NB** Before you edit your xorg.conf, back it up!```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You will find the xorg.logfile handy, it's **/var/log/xorg.0.log**. Have a look at this to see what's happening if you're forced resolution doesn't work first time.

If you kill your xorg.conf, so that you don't get any display at all, you can drop to a root prompt, by hitting 'esc' when prompted at boot, and selecting recovery console. When you get to the terminal prompt, type:```
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
to put it back. (Not you don't need 'sudo' because you're root)

The type ```
exit
``` and select resume normal boot.

HTH

Simon

---

