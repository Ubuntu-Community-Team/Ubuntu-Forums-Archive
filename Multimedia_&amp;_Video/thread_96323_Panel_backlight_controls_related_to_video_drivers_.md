---
title: "Panel backlight controls related to video drivers? (fglrx drivers)"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by Patsoe on 2005-11-28
Hi,

my short question: 

what module/component/package is responsible for making the software-based controls (Fn+F9, Fn+F10) to adjust my panel backlight work? I thought this functionality was independent of video drivers, but somehow it was lost when I switched from vesa to fglrx drivers. 

the long version, with more info:

I'm running Ubuntu 5.10 for AMD64, and installed the fglrx-drivers, version 8.16.20, as it is explained in the how-to heading this forum.

My machine is a HP nx6125 laptop, based on a Turion with ATi Express 200m chipset.

With the generic vesa-drivers, the controls (Fn+F9, Fn+F10) to adjust my panel backlight just work, 'out of the box'. Also, native panel resolution (1400x1050) is supported. This is almost perfect for me.

I installed fglrx drivers, because then I can configure a second screen, or video out. Somehow, with the fglrx drivers, the keyboard controls no longer work, and my screen defaults to maximum intensity (that is very bright!).

I tried to use fglrxconfig to create a new xorg.conf file, compared it with my original file, used several combinations of both, but nothing helps.

I don't understand how this works - which module handles the backlight control functionality? Thanks.

---

### Post by Patsoe on 2005-12-01
I'll try bumping this, just once... (sorry)

---

