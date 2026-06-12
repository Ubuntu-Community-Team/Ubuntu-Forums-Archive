---
title: "Jittery VGA display at 1680x1050"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by cojoco on 2007-06-29
Hi!

I have jittery display on a ViewSonic VA2012w, and have a new nVidia 6800 card.

I've installed the nVidia drivers using Envy, which is brilliant.

I'm using the VGA input because the DVI input is busted, but this monitor works fine otherwise ...

I've tried both 60 and 75 Hz, and they look different, but are both jittery.

Any suggestions of how to fix this, or what to tweak?

Thank you!

-peter.

---

### Post by RTrev on 2007-06-30
> **cojoco said:**
> Hi!

I have jittery display on a ViewSonic VA2012w, and have a new nVidia 6800 card.

I've installed the nVidia drivers using Envy, which is brilliant.

I'm using the VGA input because the DVI input is busted, but this monitor works fine otherwise ...

I've tried both 60 and 75 Hz, and they look different, but are both jittery.

Any suggestions of how to fix this, or what to tweak?

Thank you!

-peter.

Well, I can tell you I have two ViewSonic Q20wb DFPs, running off an Nvidia 7300 GT, and it works perfectly with the Nvidia-glx driver I got via the Restricted Drivers Manager.  If I'm not mistaken, the 60 versus 75 refresh rates you mentioned above are not applicable to DFP monitors.  Or so I've been told.  I would see if you could get the DVI input fixed.  The VGA input should look *almost* as good, and the fact that it doesn't suggests to me that perhaps more is broken than just the input itself.

---

### Post by cojoco on 2007-07-01
Fixed my problem; I had not yet tried the (manual) "Auto Image Adjust" feature on the monitor, which fixed up everything: sorry about the waste of time.

However, there was quite a noticeable difference between 60Hz and 75Hz, and nVidia Settings created two entries in my xorg.conf file for both refresh rates.

-peter.

---

### Post by RTrev on 2007-07-01
> **cojoco said:**
> Fixed my problem; I had not yet tried the (manual) "Auto Image Adjust" feature on the monitor, which fixed up everything: sorry about the waste of time.

However, there was quite a noticeable difference between 60Hz and 75Hz, and nVidia Settings created two entries in my xorg.conf file for both refresh rates.

-peter.

Super.. glad it's fixed.  Maybe the refresh rates matter when not running in Digital mode.  No waste of time.. we both learned something.  :)

---

