---
title: "Screensaver laging Ubuntu hardy"
date: 2008-08-18
forum: Multimedia Software
---

### Post by zeezam on 2008-08-18
The problem is the same as in this thread; [http://ubuntuforums.org/showthread.php?t=504067&page=2](http://ubuntuforums.org/showthread.php?t=504067&page=2)

My screensaver is laging huge in fullscren, the preview works great.

Everything else works fine, desktops effects, compiz etc.
I'm running dual screen with nvdia-settings. Have activated NVIDIA accelerated graphics driver (latest card). 

I have a Nvidia 6600 card, 4GB ram so the hardware should work just fine?
Maybe wrong drivers or software problem?

---

### Post by TenPlus1 on 2008-08-18
I have an MX400 series nvidia card which may be old but works ok in full screen, you could try going into the nvidia-settings (sudo nvidia-settings) and turning vsync for the 3D on, this way 3d runs a bit smoother and it doesn't use as much cpu time...

---

### Post by zeezam on 2008-08-18
> **TenPlus1 said:**
> I have an MX400 series nvidia card which may be old but works ok in full screen, you could try going into the nvidia-settings (sudo nvidia-settings) and turning vsync for the 3D on, this way 3d runs a bit smoother and it doesn't use as much cpu time...

Can't find any vsync option there. On which tab do you find that?

Here are som glxgears info. That last FPS output is when I ran in fullscreen.
```

14844 frames in 5.0 seconds = 2968.658 FPS
15419 frames in 5.0 seconds = 3083.759 FPS
15444 frames in 5.0 seconds = 3088.760 FPS
15803 frames in 5.0 seconds = 3160.463 FPS
15712 frames in 5.0 seconds = 3142.274 FPS
15263 frames in 5.0 seconds = 3052.425 FPS
2150 frames in 5.1 seconds = 421.585 FPS

```

I also installed the latest driver threw envyng, rebooted. Still the same.

---

