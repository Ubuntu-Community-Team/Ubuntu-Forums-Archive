---
title: "Was using S-Video a mistake?"
date: 2009-04-28
forum: Mythbuntu
---

### Post by MountainKing on 2009-04-28
I built my mythbuntu box as kind of a frankenbox (IE: a variety of parts I had lying around).  The video card I settled on was an old gaming card, probably a GeForce 6800 or something along those lines.

The outputs it had were RGB, DVI and S-Video, since I am using an older Sony CRT Television (standard Def) I really had no choice but to use S-Video even knowing it had limitations.

The trouble is, the screen is only about 80% full when I am watching MythTV or on the Mythbuntu desktop.  That is to say, the whole picture is there, it just does not fill to the edges of the physical monitor.  There is a black border around all 4 edges of the screen.

Is this indicative of a problem with:
A: the video card
B: a mythbuntu setting
C: My old CRT TV

Will I have better luck with a new card?  My TV also has component and composite ins.

---

### Post by ian dobson on 2009-04-28
Hi,

Which graphic card driver are you using? The opensource or Nvidia closesource. I would recommend you use the closed source driver.

Maybe you can adjust the picture size my increasing the resolution or playing with the scan frequency.

Regards
Ian Dobson

---

### Post by MountainKing on 2009-04-29
jeez, updating the drivers never even occurred to me... commence facepalm.

:oops:

---

### Post by SiHa on 2009-04-29
If you install the **nvidia-settings** utility (should be there with the closed-source drivers, I think), somwehere there is a slider which will allow you to increase the size. I think it's probably the overscan slider, by default it is in the midle, so you have the option to make it bigger or smaller.

---

