---
title: "Graphics card for video playback"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by fa2k on 2008-01-18
It seems that ATI will not fix the problems with the Radeon HD 2400 ([http://ubuntuforums.org/showthread.php?t=622292](http://ubuntuforums.org/showthread.php?t=622292)), even in the new 8.1 driver*. I figure I need to replace it:

**So: What is a good graphics card for video playback, that is fully supported by Ubuntu? I researched this when I bought the HD2400, so I guess I can't decide myself...**

It needs to:
- have NO artifacts during video playback
- handle 1280x720 resolution video well
- minimum CPU utilization (Xvideo or OpenGL mode support is a big plus)
- have PCI-Express interface
- supporting HDMI using a DVI adapter or directly
- have no fans or very silent ones
- be reliable in an "always on" system
- support amd64 arch

Not so important:
- compositing support
- not more expensive than necessary
- ATI has done some good for Open Source lately, so it's nice to support them


My CPU is an AMD Athlon64 3800 (single core), and I guess it's powerful enough to play the relevant videos. 

I hope someone has some tips on buying graphics cards!

Thanks,
fa2k


* According to the release notes; I can't reboot to test it, for unrelated reasons

---

### Post by Existentialist on 2008-01-25
The 8500gt from nvidia is a good card for video playback, and its in the $60-80 range.  I know there are companies that make passive cooled models too.  Here's neweggs selection:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1305520548+106791921+1067928608&name=GeForce+8500GT](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1305520548+106791921+1067928608&name=GeForce+8500GT)

Otherwise the ATI HD 2600XT would be an alright option, not as good of a value in my opinion.

---

### Post by eye208 on 2008-01-25
Nvidia's XVideo is [currently broken](http://ubuntuforums.org/showthread.php?t=675670).

Have you tried enabling vertical sync in the ATI driver (sudo aticonfig --sync-video=on, sudo aticonfig --sync-vsync=on)? Otherwise it's normal to see some tearing because most of the time the video frame rate may be different from the monitor frame rate.

---

### Post by Yellow Pasque on 2008-01-25
Try using the open-source radeonhd driver. It won't be good with CPU-utilization, but at least it should play video without tearing in vlc (it does for me).

---

### Post by fa2k on 2008-01-26
> The 8500gt from nvidia is a good card for video playback, and its in the $60-80 range. [...] 
Thanks, I'll probably try that chip

> **Temüjin said:**
> Try using the open-source radeonhd driver. It won't be good with CPU-utilization, but at least it should play video without tearing in vlc (it does for me).
I guess there is a problem with the TV and graphics card combo. I'm running radeonhd now, and the problem is different (straight lines across the screen), but not any better. I'd say it was a pure hardware issue if it did not work in Vista (it does work).

Will try to hook up a normal 17" LCD to get some more info.

---

