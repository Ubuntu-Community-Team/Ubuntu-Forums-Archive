---
title: "ATI 9500 giving me a low (?) FPS with direct rendering"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by wild_oscar on 2007-09-24
I have an ATI 9500 (and an AMD 2.6 GHz)I installed the restricted driver from synapctic, but have a low FPS rate:

glxgears gives me an average of 120-250 FPS

fgl_glxgears gives me an average of 470-600 FPS


My questions are

1) Why are there differences between the two?

2) How can I improve this score, as I see people in other threads with <1000 FPS with this card?

---

### Post by w4ett on 2007-09-24
Make sure the proper bus (AGP vs PCI)  is selected in the BIOS, also if AGP select 8X or Automatic..it sometimes help to specify the actual card video memory size in your xorg.conf.

---

### Post by wild_oscar on 2007-09-25
> **w4ett said:**
> Make sure the proper bus (AGP vs PCI)  is selected in the BIOS, also if AGP select 8X or Automatic..it sometimes help to specify the actual card video memory size in your xorg.conf.

That was already done. It seems I'm closer to the answer:

In [http://ubuntuforums.org/showthread.php?t=24557&page=11]("http://ubuntuforums.org/showthread.php?t=24557&page=11")
I see 

> Even with that I didnt have 3D acceleration, then some words got me ... you must load the ati modules before X starts. At the suggestion's of somewhere in this thread or a link from it I added the following to my .. (right at the top) ..

/etc/modules
modprobe agpgart
modprobe nvidia-agp

at one stage I also had in there but I dont think this is needed if the line fglrx is already there (which it should be)

modprobe fglrx

Before Following this Guide ( I had MESA in glxinfo instead of ATI)

1500 frames in 5.0 seconds = 300.000 FPS
1663 frames in 5.0 seconds = 332.600 FPS
1425 frames in 5.0 seconds = 285.000 FPS

After following this Guide :

28585 frames in 5.0 seconds = 5717.000 FPS
28328 frames in 5.0 seconds = 5665.600 FPS
27981 frames in 5.0 seconds = 5596.200 FPS
28063 frames in 5.0 seconds = 5612.600 FPS
28367 frames in 5.0 seconds = 5673.400 FPS
27144 frames in 5.0 seconds = 5428.800 FPS
27675 frames in 5.0 seconds = 5535.000 FPS
28200 frames in 5.0 seconds = 5640.000 FPS
28003 frames in 5.0 seconds = 5600.600 FPS
28528 frames in 5.0 seconds = 5705.600 FPS
27247 frames in 5.0 seconds = 5449.400 FPS
27760 frames in 5.0 seconds = 5552.000 FPS
27709 frames in 5.0 seconds = 5541.800 FPS
26918 frames in 5.0 seconds = 5383.600 FPS
26960 frames in 5.0 seconds = 5392.000 FPS
27392 frames in 5.0 seconds = 5478.400 FPS
28035 frames in 5.0 seconds = 5607.000 FPS
28495 frames in 5.0 seconds = 5699.000 FPS
27943 frames in 5.0 seconds = 5588.600 FPS
27991 frames in 5.0 seconds = 5598.200 FPS
28592 frames in 5.0 seconds = 5718.400 FPS
27469 frames in 5.0 seconds = 5493.800 FPS
28333 frames in 5.0 seconds = 5666.600 FPS
28165 frames in 5.0 seconds = 5633.000 FPS
28168 frames in 5.0 seconds = 5633.600 FPS
27763 frames in 5.0 seconds = 5552.600 FPS
27996 frames in 5.0 seconds = 5599.200 FPS
28405 frames in 5.0 seconds = 5681.000 FPS
28353 frames in 5.0 seconds = 5670.600 FPS
27857 frames in 5.0 seconds = 5571.400 FPS
27886 frames in 5.0 seconds = 5577.200 FPS


Which is, well...brutal!

Could it have anything to do with the

/etc/modules
modprobe agpgart
modprobe nvidia-agp

?

If I modprobe nvidia-agp, I now get:

11999 frames in 5.0 seconds = 2399.775 FPS
23520 frames in 5.0 seconds = 4703.980 FPS
22903 frames in 5.0 seconds = 4580.592 FPS
23564 frames in 5.0 seconds = 4712.659 FPS
21952 frames in 5.0 seconds = 4390.266 FPS
23705 frames in 5.0 seconds = 4740.894 FPS

After this, I modprobed agpgart and got:

19148 frames in 5.0 seconds = 3829.532 FPS
23198 frames in 5.0 seconds = 4639.430 FPS
23298 frames in 5.0 seconds = 4659.576 FPS
1859 frames in 5.0 seconds = 371.580 FPS
14474 frames in 5.0 seconds = 2894.716 FPS
23623 frames in 5.0 seconds = 4724.466 FPS
5785 frames in 5.0 seconds = 1156.816 FPS
625 frames in 5.0 seconds = 124.991 FPS
624 frames in 5.0 seconds = 124.690 FPS
624 frames in 5.0 seconds = 124.692 FPS
626 frames in 5.0 seconds = 125.191 FPS
598 frames in 5.0 seconds = 119.493 FPS

What's funny is that the huge FPS count were achieved if I have the glxgears window minimized. As soon as I see the gears the FPS drops to the 125 count...

Are these 2 modules required?

---

### Post by wild_oscar on 2007-09-25
Correction to previous post: the two modules are already loaded on startup. The difference I got in the FPS count is only due to the glxgears' window being minimized or restored. Now, a lot of fps in a minimized window is not very useful...

---

