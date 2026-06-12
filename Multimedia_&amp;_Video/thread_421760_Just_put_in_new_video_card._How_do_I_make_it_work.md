---
title: "Just put in new video card. How do I make it work?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2007-04-24
I've just physically installed a new PNY nVidia GeForce 6200 card (replacing my very old ATI which is no longer supported by fglrx).

I knew I'd have to do things on the software side, but what's first?  I have the errors you'd expect from Xorg (since I swapped the card already), but don't know how to proceed.  If it's just a matter of editing Xorg.conf, what do I type?

Or is there some "update" procedure I can follow to get X to recognize my new card automagically?

Thanks for any help you may have!

-Mark

---

### Post by ac7ss on 2007-04-24
from the  prompt type ```
sudo dpkg-reconfigure xserver-sorg
``` and let it do it's thing.

---

### Post by sisco311 on 2007-04-24
and select the nv driver

---

### Post by ac7ss on 2007-04-24
> **sisco311 said:**
> and select the nv driver

or the nvidia (I don't know which model uses what.)

---

### Post by mjpatey on 2007-04-24
Thanks!  I answered a question wrong the first time through the reconfigure process... I said "Yes" to "Use kernel framebuffer device interface?"  When I went through a second time and answered "no," I was finally able to boot all the way into X and Gnome.

Unfortunately, e-v-e-r-y-t-h-i-n-g  is really  s-l-o-w... much slower than with my ancient ATI card.  I'm thinking that the system is ignoring the card's processor, because everytime I move a window around, it brings my CPU to 100% ("both" CPUs; I have a hyperthreading 3.2GHz Pentium 4).  Everything is terribly jerky and slow, 3-D screensavers go at about 1 frame per second, GLXGEARS reports 159 fps (but displays about a frame per second if that, and my old ATI used to register in the 1600-ish range).

Now I know this isn't how my nVidia card is supposed to look... anybody know what I should do to make it work for real?  It's only a 6200 with 256MB of RAM, but it should be doing better than this for sure.

Thanks for any help you may have!

-Mark

---

### Post by ac7ss on 2007-04-24
Are you using the nvidia driver? or the NV driver. With my (built in) nvidia GEForce 6100 I use the nvidia driver. It works like a charm. (I even get the Nvidia logo as X starts.)

---

### Post by Syke on 2007-04-24
Sounds like it's using neither nv nor nvidia. I'm guessing vesa. What does the "driver" line say in xorg.conf?

---

### Post by mjpatey on 2007-04-25
It is set to "nvidia"... and it now works like a charm!  I went through the "desktop effects" option, which automatically installed the accelerated driver.

Is this the best driver available for my 6200?  I'm pretty happy with the acceleration, but it's not much better than what I used to be able to get with my ATI back when it was supported by fglrx.  Is there another proprietary nvidia driver that accelerates more, or is this the best?

Thanks!

-Mark

---

### Post by Syke on 2007-04-25
That's probably as good as you'll get. The 6200 is pretty low-end for it's generation.

---

### Post by mjpatey on 2007-04-25
Syke, what would you recommend for Ubuntu Feisty in the $100-ish range?

---

### Post by Syke on 2007-04-25
I'm guessing you have an AGP slot. You're kind of limited in your selection if you've still got an AGP slot. A Nvidia 7600 GS would be right around your price range.

If you do have a PCI express slot, you could step up to a 7600 GT for about the same price.

---

### Post by RAKninja on 2007-04-25
I tried 7.04, and 6.10, and i cant get my PCI 6200 to work, whats more, if i change BIOS settings to make the PCI GFX controller the primary GFX, ubuntu has page faults that terminate startup at 3 bars on the loading screen.

---

### Post by ac7ss on 2007-04-26
while the splash screen is up, press <ctrl><alt>F1 then <alt>F7 this will display the progress and can identify the point where the system crashes.

---

### Post by RAKninja on 2007-04-28
it goes by too fast. all i can see is that its a page fault.

though screenshots almost identical to my display are on this thread

[http://ubuntuforums.org/showthread.php?t=416859](http://ubuntuforums.org/showthread.php?t=416859)

---

### Post by mjpatey on 2007-04-28
Syke,

Thanks again... I'm going to stick with the AGP 6200 until I get a new motherboard with PCI Express.  By then, maybe the 8800 cards will be a little cheaper!

-Mark

---

