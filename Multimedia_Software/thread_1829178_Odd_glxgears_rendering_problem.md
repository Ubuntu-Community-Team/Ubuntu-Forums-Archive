---
title: "Odd glxgears rendering problem"
date: 2011-08-20
forum: Multimedia Software
---

### Post by Keith_Beef on 2011-08-20
I just updates to 11.04 from 10.10 and glxgears is exhibiting very peculiar behaviour.

When I run glxgears, I see reported very high frame rates, but the image rendered is not moving at all unless I resize the window, and then it is not a smooth image of gears turning, but is seems to "skip" several hundred or thousand frames.
```

$ glxgears
38895 frames in 5.0 seconds = 7778.917 FPS
39541 frames in 5.0 seconds = 7908.118 FPS
39300 frames in 5.0 seconds = 7859.937 FPS
39566 frames in 5.0 seconds = 7913.146 FPS
39974 frames in 5.0 seconds = 7994.706 FPS
40012 frames in 5.0 seconds = 8002.205 FPS
39703 frames in 5.0 seconds = 7940.465 FPS
39944 frames in 5.0 seconds = 7988.745 FPS
40002 frames in 5.0 seconds = 8000.226 FPS
^C
```

Any idea what the problem is?

Look in my sig for hardware details.

---

### Post by BicyclerBoy on 2011-08-20
glxgears is not a performance metric..

It is just a tool to check vsync setting & general openGL is functional.

Your video card is so fast you see a strobed effect.
Your card is able to redraw 100 frames per refresh cycle..so no problem..

---

### Post by Keith_Beef on 2011-08-20
> **BicyclerBoy said:**
> glxgears is not a performance metric..

It is just a tool to check vsync setting & general openGL is functional.

Your video card is so fast you see a strobed effect.
Your card is able to redraw 100 frames per refresh cycle..so no problem..

I thought that this might be the case, but with 10.10 I got very similar frame rates and smooth animation.

---

### Post by BicyclerBoy on 2011-08-20
There could be some issue with unity/compiz 11.04..

My 11.04 PC  (i3 with old obsolete 9400GT) gnome2 classic, unity & compiz un-installed, animates the glxgears okay but it only does 170fps full screen 1550 fps small window..

---

### Post by Slart on 2011-08-26
> **Keith_Beef said:**
> I just updates to 11.04 from 10.10 and glxgears is exhibiting very peculiar behaviour.

When I run glxgears, I see reported very high frame rates, but the image rendered is not moving at all unless I resize the window, and then it is not a smooth image of gears turning, but is seems to "skip" several hundred or thousand frames.
```

$ glxgears
38895 frames in 5.0 seconds = 7778.917 FPS
39541 frames in 5.0 seconds = 7908.118 FPS
39300 frames in 5.0 seconds = 7859.937 FPS
39566 frames in 5.0 seconds = 7913.146 FPS
39974 frames in 5.0 seconds = 7994.706 FPS
40012 frames in 5.0 seconds = 8002.205 FPS
39703 frames in 5.0 seconds = 7940.465 FPS
39944 frames in 5.0 seconds = 7988.745 FPS
40002 frames in 5.0 seconds = 8000.226 FPS
^C
```

Any idea what the problem is?

Look in my sig for hardware details.

I've got the exact same problem.. the glxgears animation hardly moves but the fps numbers are ok.

I'm running ubuntu 11.04 but I've uninstalled unity and I'm running compiz with a modest set of effects. Graphics card is a Nvidia 470 gtx with the nvidia binary driver 280.13.

/Slart

---

### Post by BicyclerBoy on 2011-08-26
I'm not sure anything is wrong..
glxgears is not a real performance metric.

If you enable sync-on-vertical-blank for openGL, then you should get 60 fps (or it should match your screen refresh rate).

Does the glxgears animation look smooth with vsync on?
This is the normal setup for openGL.

I believe compiz has/did have a problems detecting the correct refresh rate from the nVidia driver. You have to set it manually via CCSM ?

FWIW (very little)
11.04 unity3d, compiz, intel GMA950, i915 driver, vsync & glxgears all seem to play together okay ..(albeit very slowly)

---

