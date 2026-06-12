---
title: "Video playback quality/performance issues"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by pormogo on 2007-05-07
Earlier I had an issue getting video playback to work with the libgl-mesa-dri radeon driver on 7.04, I was able to find a fix for this issue. By changing VLC's output module from default to X11 video now does work on my box but just barely =P 

Video playback (from dvd, or multimedia container) is poor. The quality is pixely and the the playback is choppy. It is not uncommon to see the following 

[i]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
18116 root      17   0  485m 162m  14m R 70.5 10.7   7:16.02 Xorg               
20212 darthbat  15   0  192m  49m  23m S 21.0  3.3   1:59.93 vlc  [/i]

it seems that Xorg is eating crazy amounts of CPU time when playing video.... I am running a reasonably current version of the kernel (2.6.20.3) compiled for my machine. Is this just kinda what we're stuck with until ATI can get around to releasing a driver with compositing support :(

---

### Post by pormogo on 2007-05-09
No ideas? Anyone else here using the open source driver and AIGLX? Are you guys having multimedia performance issues as well?

---

### Post by bubbalouie on 2007-05-10
Yes! 

My media box is back to  OEM XP, I bought a new PC (Nvidia and creative parts to avoid driver issues) and a fairly good LCD in the hope of finally getting a decent media system up and running. The unfixable video tearing and occasional choppiness on a fairly grunty system was a real disappointment (1gb ram, SATA drives, 3ghz CPU and geforce FX5200 should be able to play a 640x320 divx scaled to 1360x768 with ease, but feisty couldn't cope).

That said, it can usually be improved by:

Installing proprietary drivers
Syncing to vblank (openGL and video textures)
Enabling triple buffering
enabling direct rendering
Using the right output 'device' in your chosen media player

---

### Post by bubbalouie on 2007-05-10
Forgot to mention, I am unsure if ati does triple buffering sorry, off hand the ati-config tool offers tips on how to do the syncing stuff when you ask it for help from the console

---

### Post by dodgePT on 2007-05-10
I'm running open source drivers (radeon driver) with AIGLX, since everything seems stable and beryl desktop works without hanging. I did not get the same results with fglrx + XGL, since it crashed my X from time to time.

**[COLOR="Red"]BUT[/COLOR]** _movie playback issues remain_, and there's no solution (to my knowledge). Video is blocky using X11 codec in fullscreen mode, and colors are strange.
I usually reboot my machine and watch my movies in WindowsXP, since i've a 42" LCD television  connected through DVI (which brings another issue about ATI, and a "scandal" regarding hdmi support, but that's another story).
That seems to be the only solution if you intend to keep beryl installed and running, at least untill ATI releases better drivers (although i lost all hope) or allow for 3rd party to develop their proprietary drivers (which seems to be a dead end too).

In July i'll be doing an hardware upgrade and ATI graphics adapter is not in my list for sure. This time i'll be going to NVidia :)

---

