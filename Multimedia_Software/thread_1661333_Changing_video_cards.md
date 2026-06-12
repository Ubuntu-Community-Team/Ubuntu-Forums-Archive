---
title: "Changing video cards"
date: 2011-01-06
forum: Multimedia Software
---

### Post by ghostmonk on 2011-01-06
Hello all,

I got it into my head to change the graphics card in my Ubuntu 10.04 media center.  I removed my old ATI card and installed a new ASUS ENGT 430.  I tried to uninstall the ATI drivers and associated software prior to this but obviously I didn't get it all.

When I boot into X it takes me in under low graphics mode.  I've tried rebuilding my xorg.conf.  I've installed the driver from the ASUS site and nothing.

I decided to swap in my old ATI card and obviously I've not cleared all the ATI artifacts as the low graphics mode that machine first booted into was at the high resolution that I was running previously.  I uninstalled all Nvidia software but now I'm not even able to get the old ATI software to work.  Jockey sees the drivers after I install them through the Software Center but they're not really working.  XBMC won't start for GL reasons.

What do I need to purge all graphics drivers and install the nVidia driver?  I've got a feeling if I started from scratch I could get it to work but I seriously don't want to reinstall everything.  I've worked hard to get my XBMC config just so and I don't want to lose everything.  Help!

---

### Post by BicyclerBoy on 2011-01-06
There is NO linux driver from asus.
You need a newer graphics driver than std *buntu.

Stick the nvidia card back in & move/backup your xorg.conf file (delete original).

You need the driver (version 260) from nvidia or the ubuntu X team

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

This ppa is much easier to use than nvidia install.

You need (must have) kernel headers that match your running kernel.
uname -r

---

### Post by moodog on 2011-02-06
Did you end up resolving this? I had the same problem (going from NVidia 6200 to gigabyte (nvidia) gt430. Failed to load properly, added the new PPA, updated to 270.18, but still failing.

---

