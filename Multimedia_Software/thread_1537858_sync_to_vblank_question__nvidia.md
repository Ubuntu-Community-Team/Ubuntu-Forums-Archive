---
title: "sync to vblank question / nvidia"
date: 2010-07-24
forum: Multimedia Software
---

### Post by c.dric on 2010-07-24
Hi all, 

I'm trying to get the best performance/quality on my my 10.04 box and i have a few questions regarding 'sync to vblank'. Maybe someone can help.

My first question : I see 'sync to vblank' in 3 different locations. 
- In compiz display settings
- In NVidia XVideo settings
- In NVidia OpenGLX settings
What is the difference between the 3 ?

Second question : I used to have problems watching movies where the picture seemed to be cut in half ( i'm not a native english speaker so i don't know the technical term). After reading some forums, i enabled sync to vblank everywhere i saw it. That solved the movie problem. But maybe that was overkill ??

So i did some benchmarking and noticed the following : 
When i disable 'sync to vblank' in compiz my compiz benchmark drops from 60 to 30. But then my movies look worse.
When i disable 'sync to vblank' in NVidia OpenGlx my GlxGears framerate jumps from 300 to 36000.
I didn't notice anything when changing vsync in the NVidia XVideo setting.

Nothing critical here but i would appreciate if someone could clarify the situation a little bit for me. System specs below.

Ubuntu 10.04 64b
Nvidia GT 230 1536MB
NVIDIA Driver Version : 195.36.24

Thx.

---

### Post by RaumTrug on 2010-07-25
hi cedric.

you probably know what a "vblank" is? if not: the display of your monitor gets updated at a certain interval. say 60hz, so 60 times a second. when updating, the graphics card sends, synchronized with the display/monitor,  every pixels color value from the currently visible graphics memory to your screen, rowwise from the upper left corner to the lower right corner. it does that for the whole screen 60 times a second if the refresh rate is 60hz. now, the update doesn't take 1/60 second but less, and the period during which no pixels are sent to the monitor is called a "vblank", i.e. the graphics-card to monitor traffic is idle during that period. the name "vblank", i.e. "vertical blank" comes from the fact that during that period, on old tube-crt screens, the cathod ray beam was turned off and moved from the lower right corner to the upper left, called a "retrace". there's also a "hblank", but that is (ab)used only by real hackish/old software, and yes, lcd displays also work this way, more or less...

so what's the benefit of the application being aware of a "vblank" and sync to it? simply, if you write your graphics data to the videocard while the stuff is being read by the monitor, there will be 2 versions of graphics visible: the old "frame" to the point where the monitor was reading untill the write/update, and below that the new frame. that's when "tearing" will happen, and animated visuals will seem like horizontally split. however, if a program updates the graphics during a "vblank", i.e. while the screen is still displaying the last frame, and before it reads the next, no tearing will happen, and animation will seem a lot more appealing to the eye. no more split visuals, all creamy.

so "sync to vblank" options makes applications wait for the retrace of screen, and each component in your driver/application setup you turn that option on should be fixed (if slower, it drops frames, but should still not tear) to the monitor refresh rate. that's good for your eyes... ;)

"nvidia xvideo" syncing will affect video playback (of video/movie files), if the program playing back uses the x-server "xvideo" (short xv) extension. there's also few progs that use that extension for non-video graphics, but I can't think of one right now...there's, for me, a "video texture"-mode, and a "blitter" mode, I guess the video texture is the most commonly used thing...it depends a lot on the application, some can be setup to use opengl for video playback, too.

the "opengl" vblank syncing affects all 3d rendering, and also other progs (see above) using opengl for other graphics rendering, i.e. 2d, or even videos. glxgears gives a million fps without syncing, because it can render as fast as possible. with syncing, the programs wait for vblank before updating, fixing to the 60 frames per second corresponding to the 60hz of your monitor. games don't need to run faster that the refresh rate, you wouldn't really notice the difference, it's just cool to disable sync to see how fast it can go ;) ...if your graphics card was much slower, or you ran something really using 3d to the maximum, it'd probably not run at 36000fps but at 60.5 fps and you'd get real bad tearing!! 36000 fps is such a high value that you won't notice the tearing anymore, each frame of you monitor will show part of a few hundred frames of opengl graphics, getting newer from top to down. btw, you save energy by syncing, as cpu & gpu can idle & stay cool instead of rendering unneeded surplous frames of 3d visuals all the time. clever opengl apps can enable/disable syncing by themselves, normally.

...like compiz can, but there seem to be bugs somewhere, as you said when turning on you get 60 fps (the refresh rate, so syncing should be fine), and 30 with syncing turned off (i.e. the system is waiting for 2 retraces for every update, and that'd suck big times!!!). I guess compiz sync synchronizes all other graphics updates, i.e. the whole desktop and the desktop effects. normally with syncing turned off it should render frames like mad, so something might be wrong there, seriously.

I hope this clarifies some things for you, just fiddle to have sync properly wherever possible (videos, 3d, desktop fx), it's better for the eyes 8)

---

### Post by c.dric on 2010-07-26
Hi RaumTrug

Thanks for taking the time to clarify this. I really appreciate.
I'll leave 'sync to vblank' on then, as it looks like the best deal ;)

Just one thing :

> **RaumTrug said:**
> 
...like compiz can, but there seem to be bugs somewhere, as you said when turning on you get 60 fps (the refresh rate, so syncing should be fine), and 30 with syncing turned off (i.e. the system is waiting for 2 retraces for every update, and that'd suck big times!!!). I guess compiz sync synchronizes all other graphics updates, i.e. the whole desktop and the desktop effects. normally with syncing turned off it should render frames like mad, so something might be wrong there, seriously.

It's actually the opposite in my case. With sync on, my compiz framerate is 30, when turned off it goes up to 60.

Thanks again.
Cédric

---

