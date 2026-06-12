---
title: "XWAX assignment to freebob ( alsa to jack ? )"
date: 2007-10-06
forum: Multimedia Production
---

### Post by Stochastic on 2007-10-06
Okay so I'm wondering if there's a way to route an alsa app such as XWAX - ok more like specifically XWAX but it'd probably be the same for any - where you're supposed to assign the device of your choice (the examples at [http://www.xwax.co.uk/guide.html](http://www.xwax.co.uk/guide.html) say /dev/dsp and dev/dsp1) into jack or any freebob device?  I'm running UbuntuStudio Feisty.

---

### Post by Stochastic on 2007-10-08
So I've solved this issue and thought others might want to try this.  There's a development branch of the XWAX software that has jack support but a trick to get it running on ubuntu is to do ```
sudo ln -sf /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
``` and after that all that's left is to run the software with ```
./xwax -l <path to music library> -j <# of decks>
``` I also found that you need to hit play on qjackctl transport to get it to work.  I'm quite pleased with this software and hope to see it put into UbuntuStudio repos for the next (not gusty but the one after) release, but like I said, it's developmental... pros only...  don't try this if you don't know how to speak code.

---

