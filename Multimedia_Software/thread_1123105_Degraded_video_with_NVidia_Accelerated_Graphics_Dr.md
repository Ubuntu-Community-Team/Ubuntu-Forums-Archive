---
title: "Degraded video with NVidia Accelerated Graphics Driver 180"
date: 2009-04-11
forum: Multimedia Software
---

### Post by Dngrsone on 2009-04-11
Has anyone noticed a degradation in their video when upgrading to the new Nvidia 180 restricted driver, or is it just me?

My wallpaper is a photograph and I noticed that after the upgrade the image was pixelated a little, like it's using only 16 bit instead of 24.

When I donwgraded to 177, the image looks normal.

I am running Ubuntu 8.10 on an HP DV2214us Pavilion laptop with NVIDIA GeForce Go 6150 graphics and a 14.1" 1280x800 display.

---

### Post by steeeb on 2009-04-12
Same problem here.  I tried changing to 24 bit but it was already set.  I switched back to 177 and my background looks just fine now

---

### Post by Dakiraun on 2009-04-13
Same issue here.  I had been running version 173 on my laptop, which has a Nvidia Quadro FX 350M GPU.  When I upgraded to 180, it looked like it was running in 16 bit mode as all the shading on the background and theme gradients was very rough.  

I tried using the nvidia Display manager to check the settings and found it claimed (or at least thought) it was running in 24 bit mode.  I even went so far as to try hard-coding the 24 bit depth into the Xorg.conf, but it had no affect.  Only by rolling back to version 173 did I get back the proper colour depth.

Has this been acknowledged as a known bug yet?

---

### Post by Dngrsone on 2009-04-13
Good question.  A quick search on Launchpad for NVidia 180 graphics drivers shows a 117 bugs or so, but none appeared to be of the same nature as this.

---

### Post by Dakiraun on 2009-05-01
I guess the relative silence on this means there are no fixes for the issue.  Hope the next one works. :/

---

### Post by Guilden_NL on 2009-05-01
Or the size of the problem is smaller than it may appear.  I have no problems with the 180 driver, in fact, mine appears to be clearer than before.  Could be differences with cards.

I run a eVGA GeForce 7800 GT 256MB on the system I've upgraded using an NVidea driver.

---

### Post by Dakiraun on 2009-05-12
Interesting update - after upgrading to Jaunty Jackalope, the issue with the 180 driver went away.  So seems to be very version and hardware specific.

---

