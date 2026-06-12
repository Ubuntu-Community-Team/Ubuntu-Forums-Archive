---
title: "input signal out of range"
date: 2010-12-24
forum: Multimedia Software
---

### Post by VideoAddicted on 2010-12-24
Whenever I try to play games with a higher graphical requirement from my system, I get the error "input signal out of range".  

In particular, I get this error with the games Egoboo and World of Goo (both from repos).

I do not get this error when I do not use graphics drivers, but when I don't, although I have some video output, I'm at somewhere around 1.2 fps.  

My monitor is a HannsG HW191A and I am running 10.10.

Any help would be appreciated.

---

### Post by thedrachen on 2010-12-29
I have a similar problem, except I will get a signal out of range error at random. I will be looking at these forums or even out of the room. I also have a Hanns G monitor, HW173D. I'm running Lucid Lynx.

---

### Post by Kranix on 2011-01-07
Same problem here; I experience it with [COLOR=black]*Egoboo *[/COLOR]and *Extreme Tux Racer*.

---

### Post by BicyclerBoy on 2011-01-07
Sound like the monitor is not able to display the video mode that the game has selected.

The root cause must the video mode validation from EDID DDC monitor information.

Could be the X server error
Could be bad monitor EDID data.

You can (with nvidia-settings at least) force the GPU (video card) to do all scaling & always output the display native resolution.
Make sure you select the native panel res for your default video mode.

Depending on how good your video card is, GPU scaling to native will always be better PQ.
This may reduce the max possible fps but you will be able to use all video modes.

---

