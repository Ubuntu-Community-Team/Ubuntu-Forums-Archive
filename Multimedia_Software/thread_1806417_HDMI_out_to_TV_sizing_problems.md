---
title: "HDMI out to TV sizing problems"
date: 2011-07-17
forum: Multimedia Software
---

### Post by Rikeshar on 2011-07-17
Hey everyone, I've googled around (weird that that's a verb) on this issue and can't seem to find a solution. I'm using an Nvidia GeForce GT 430 graphics card with an HDMI out port. I've got an HDMI cable connected to my TV, a Panasonic TC-P42X1. The quality is great, the audio works fine, however the screen sizing is off. It's cutting off a top-panel-height from the top and bottom, and roughly the same on each side as well. 

I've changed the screen resolution, changed the TV sizing options (zoom, full, just, etc.) and checked around in the Nvidia settings with no change.

Does anyone have any idea on how to fix this?

---

### Post by Rikeshar on 2011-07-21
Anyone have any suggestions about this?

---

### Post by Rikeshar on 2011-08-07
Issue resolved. In the nVidia settings, under the GPU section on the left, there's a slider for overscan compensation. This is what adjusts the sizing.

---

### Post by solitaire on 2011-08-08
Does the changes survive a reboot?

---

### Post by BicyclerBoy on 2011-08-08
The better solution is to configure the TV to use no overscan mode.
You lose PQ by GPU scaling & then have the TV scale it back again..

Due to marketing dept this can be called:
justscan
PC input mode
no-overscan (great idea)
direct pixel mapping
some-other-silly-name

You can improve the PQ by using YUV colour-space instead of RGB..
It may already be using this..

---

### Post by Rikeshar on 2011-08-09
It did survive at least one reboot, so I'm hoping it won't be a problem.


As for the overscan on the TV end, I couldn't find any option on my TV. I don't remember the exact model right now (I'm not at home) but it is a Panasonic. I did look though!

---

### Post by BicyclerBoy on 2011-08-09
On the newer panasonic plasmas V20 you have to go into professional mode before all the useful calibration & just-scan is available..

---

