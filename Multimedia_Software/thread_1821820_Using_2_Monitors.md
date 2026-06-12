---
title: "Using 2 Monitors"
date: 2011-08-09
forum: Multimedia Software
---

### Post by Stagleton on 2011-08-09
I just got a new graphics card which shouldnt be the problem directly. The card is a NVIDIA GTX 460 and I updated the graphics driver. Both screens look great except for some reason I can't drag other windows into the second window. My mouse goes into the second window, but not any windows....

Has anyone had this problem or know how to fix it?  [-o<

I tried searching but I couldnt find it...hard to get the right key words I think

---

### Post by Stagleton on 2011-08-10
hmm, any ideas?  :-k

---

### Post by BicyclerBoy on 2011-08-10
That is separate X screens..
I find it ideal for full screen video..just need to know how to get apps to launch on it..
DISPLAY=":0.1" vlc

run the nvidia-settings GUI tools & try twinview..
This is not without its own problems...

Multi-displays does not really work with nVidia (linux) on consumer video cards.
Xorg X server is could be part of the problem.

A good nVidia soln is mosaic (base & SLI) but is only available on quadro cards (money).

---

### Post by Stagleton on 2011-08-15
cool, that worked. changing the monitor configuration to TwinView solved my problem! 

thanks!


:guitar:

---

