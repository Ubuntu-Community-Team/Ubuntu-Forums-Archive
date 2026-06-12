---
title: "Slow graphical performance with Meerkat"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zmb0386 on 2010-09-19
Hi all, I upgraded to the Meerkat beta from Lucid yesterday, and I've been noticing pretty poor performance from Compiz and the like.  I've got a very recent nVidia card - GTX 260 - and Additional Drivers reports that the latest ("version current") proprietary nVidia driver is installed and working.

If this is just a beta thing, that's fine, but is there something I can do to try and figure out what's causing the slowdown?  Even simple stuff like scrolling in Firefox is fairly sluggish, and the more complicated Compiz effects that were working great in Lucid are extremely choppy.

---

### Post by NightwishFan on 2010-09-20
I would wait it out perhaps try to reinstall the nvidia driver just in case. Also you could try playing with the Nvidia Settings.

---

### Post by lovinglinux on 2010-09-21
I think there are some issues with the nvidia driver. Check the stickies for info about known issues.

I'm back to Lucid btw and I will probably skip this upgrade.

---

### Post by zmb0386 on 2010-09-23
Thanks for the tips.  There are indeed problems with the nvidia driver and the new xorg.  I did some poking around and read that the beta driver fixed this issue, so I gave it a try.  And I'm happy to report that it worked, and now everything's rendering briskly again.

Beta driver is here:
[http://www.nvnews.net/vbulletin/showthread.php?t=155137](http://www.nvnews.net/vbulletin/showthread.php?t=155137)
(Bugfix of interest: Fixed an interaction problem with a change in X server behavior that caused slow text rendering on X.Org xserver 1.9.)

Instructions on installing it are here:
[http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/](http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/)

I wouldn't really recommend it to someone new to linux, but it worked well enough for me.

---

### Post by VinDSL on 2010-09-24
> **zmb0386 said:**
> I did some poking around and read that the beta driver fixed this issue, so I gave it a try.  And I'm happy to report that it worked, and now everything's rendering briskly again.[...]Glad I kept reading!  

I was going to suggest purging the canned drivers and installing the latest factory beta version.

One last note...

I ran some tests, using GtkPerf, and there is a 35% increase in speed, by specifying "Best Contrast" font rendering in "Appearance Preferences" compared to "Subpixel smoothing (LCDs)".

And, yes, I'm running a TFT monitor.  Text looks fine...  :)

---

### Post by DodgeV83 on 2010-09-24
> **zmb0386 said:**
> Thanks for the tips.  There are indeed problems with the nvidia driver and the new xorg.  I did some poking around and read that the beta driver fixed this issue, so I gave it a try.  And I'm happy to report that it worked, and now everything's rendering briskly again.

Beta driver is here:
[http://www.nvnews.net/vbulletin/showthread.php?t=155137](http://www.nvnews.net/vbulletin/showthread.php?t=155137)
(Bugfix of interest: Fixed an interaction problem with a change in X server behavior that caused slow text rendering on X.Org xserver 1.9.)

Instructions on installing it are here:
[http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/](http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/)

I wouldn't really recommend it to someone new to linux, but it worked well enough for me.

Thanks for this!  Was about to quit 10.10 completely, but the beta drivers work wonders for my Dell Studio XPS 13 :)

---

