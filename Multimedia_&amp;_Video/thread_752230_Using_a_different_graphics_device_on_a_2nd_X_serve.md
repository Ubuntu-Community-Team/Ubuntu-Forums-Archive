---
title: "Using a different graphics device on a 2nd X server"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by Kosherbacon on 2008-04-11
Hello,

I have a Toshiba Tecra A4 laptop with an nVidia GeForce 6600.  No matter how many config guides I have read or little tweaks I have tried (xorg.conf tweaks, upgrading to newer nVidia driver, etc) I have never gotten my Ubuntu 7.10 to scale low, square-aspect resolutions such as 640x480 to fit the screen.  The top and bottom of the logical screen isn't displayed on my widescreen DFP.

I have also experimented with the display settings with nVidia's tool and by hand-editing the conf file, but that didn't help either.

This is only a problem for me with older/retro-styled 2d games that don't require any kind of acceleration AFAIK.  For now I've just been invoking xrandr to set a closer resolution and play it windowed (800x600), but that's not really ideal.

I have read about setting up a second X server; is it possible to set one up to use either a generic VESA driver (or even Xvesa instead of X.org) or my integrated Intel graphics instead of a specific driver for the nVidia?  I'm not sure what driver Ubuntu used on the liveCD/install, but I believe it was set to 640x480 and scaled to fit the screen just fine.

Thanks in advance,
~Colin

---

