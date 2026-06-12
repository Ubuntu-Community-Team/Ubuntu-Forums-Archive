---
title: "Composite Extension Problem"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2006-08-28
Hey,

I have an ATI Radeon Xpress 200 chipset ([http://www.ati.com/products/radeonxpress200Intel/specs.html](http://www.ati.com/products/radeonxpress200Intel/specs.html)), and I'm running Xubuntu. What I'm trying to do is enable Composite and be able to use some of the effects that come with that. for starters, i'll use xfwm4, and then move on to compiz. I've already checked out what kind of drivers I will need, and i've tried a couple of solutions. (The [proprietary drivers]("http://ubuntuforums.org/showthread.php?t=204910") and the open source ati driver).

So this is my dilemna: when I use the "ati" driver, i have no hardware acceleration, and thus enabling Composite has no effect. When I use the proprietary fglrx driver, I can't enable the composite extension because when i do my desktop gets all screwed up. So basically, I need another way out. any ideas as to what my next step should be? 

thanks

---

### Post by maniacmusician on 2006-08-28
I don't know if this means anything, but when I run lspci | grep VGA, i get 

```
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a61

```

the "Unknown device" part seems kind of fishy. I googled the last bit (Unknown device 5a61) but didnt come up with anything significant.

edit: some more info. As the specs page said, the integrated graphics are Radeon X300 based. that card is supported by the open source driver "radeon", but only 2D acceleration is available (I want 3D). it's not technically supported by the "ati" driver. 

The proprietary drivers that i have installed (fglrx) are supposed to fully support my Radeon Xpress 200 Chipset ([https://www2.ati.com/drivers/linux/linux_8.26.18.html](https://www2.ati.com/drivers/linux/linux_8.26.18.html) ,down where it says Integrated Product Support). but obviously something is wrong if i cant even enable compositing.

---

### Post by maniacmusician on 2006-08-29
I think that the ati drivers are definitely my problem in being able to enable compositing. here is what glxgears shows me:
```

1787 frames in 5.0 seconds = 357.382 FPS
1748 frames in 5.0 seconds = 349.435 FPS
1757 frames in 5.0 seconds = 351.331 FPS
1757 frames in 5.0 seconds = 351.284 FPS

```

i also did fgl_glxgears and got:
```

Using GLX_SGIX_pbuffer
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
60 frames in 5.0 seconds = 12.000 FPS
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
844 frames in 5.0 seconds = 168.800 FPS
1868 frames in 5.0 seconds = 373.600 FPS
2366 frames in 5.0 seconds = 473.200 FPS
2359 frames in 5.0 seconds = 471.800 FPS
2365 frames in 5.0 seconds = 473.000 FPS
2364 frames in 5.0 seconds = 472.800 FPS

```

I don't think those numbers are very good. But i can't figure out what tweaking i have to do to fix it.

---

### Post by bramble on 2006-09-05
I am having a similar problem... 

have you tried mounting a tmpfs ?  

add this to /etc/fstab

tmpfs /dev/shm tmpfs defaults 0 0 

then 

mount /dev/shm

---

### Post by maniacmusician on 2006-09-05
what is this supposed to fix? sudo mount /dev/shm didnt give me any errors, but when i ran glxgears again, i got the same numbers, more or less. if you mean the composite thing, i have to restart x for that, so i'll go try that right now.

edit: composite extension still does not work. but my desktop does seem to load a little bit faster. thanks for trying though.

---

### Post by SamSpade on 2007-10-25
Greetings,

I have not seen anything really useful posted on the net with regards to this problem:

fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!

In general the ATI GL drivers are really really good and highly configurable. And I am impressed by the broad range of hardware that is supported by the fglrx driver.

Enough said...

most frequently the error:

fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!

Arises from poor configuration of the fglrx driver in the x server configuration file (xorg.conf). Some configuration flags are contradictive and since the fglrx driver performance and behaviour is highly hardware dependent it is important that you carefully check that you have hardware that supports your configuration of fglrx.

The most common problem is that you have both options:

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"

This is not possible and in some cases the driver is not able to automatically disable one of the above.

Another such configuration problem can be:

Option "Stereo" "on"

without having stereo support in the hardware.

So - check your fglrx configuration carefully. Start with enabeling a minimal set of GL features if you are unsure about what is supported on your card.

Regards -- Jan (SamSpade)

---

