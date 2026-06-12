---
title: "Can't change brightness in videos in Ubuntu 6.10 after I install nvidia's driver"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by John Doe on 2007-01-07
When doing a test installation of Ubuntu 6.10, I encountered a rather weird issue that happens only after I install nvidia's driver.  After installing nvidia's driver, when I play videos in Totem and try to adjust the brightness of the video (Edit menu, Preferences, Display tab) since videos play rather too dark on my system by default, the sliders for the brightness settings seem to not do anything and the video stays dark even if I move the brightness slider all the way to the right.  If I go and uninstall nvidia's driver and switch back to the "nv" driver, the brightness slider in Totem works and I can successfully adjust brightness of videos.  Does anyone know why I can't adjust brightness in videos only when I have nvidia's driver installed?

---

### Post by david_2001 on 2007-01-08
This has been discussed recently.  Take a look at [http://www.ubuntuforums.org/showthread.php?t=288363](http://www.ubuntuforums.org/showthread.php?t=288363)

I haven't bothered with the fix and just use nvidia-settings to change brightness, contrast, gamma etc. when necessary.

Even if it only has novelty value, the X Composite extension means that screenshots including a running video application no longer have a blue rectangle where the picture is being drawn.

---

### Post by John Doe on 2007-01-12
Thank you!!!!!  Running "sudo nvidia-xconfig --no-composite" in Ubuntu 6.10 did the trick and I can now adjust the brightness of videos I play!  

On my setup, if I use "nvidia-settings" and brighten up my entire screen to get videos to the proper brightness, other stuff on my screen ends up being way too bright (almost as if I am staring at a very bright light bulb for stuff that isn't a video, while videos played inside Totem appear at a normal/decent brightness).  So, I needed a way just to get the brightness to work for videos only and not my entire screen.

---

