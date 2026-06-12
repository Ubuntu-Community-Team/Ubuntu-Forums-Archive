---
title: "Bad Video Playback in TwinView"
date: 2009-09-29
forum: Multimedia Software
---

### Post by dsevastakis on 2009-09-29
hi, i have posted this before but it seems that it has been forgotten by the world:/ 
i have 2 screens connected on my PC, 19" 1280x1024 75Hz, and 32" 1369x768 60Hz.
when i have only one of the screens activated, video playback is perfect, no problems.. but as soon as i enable the second screen in TwinView, i get this horizontal lines across the screen which is very annoying.. any ideas?
i already tried setting monitors on same frequency and from the compiz settings manager to set refresh rate on the same frequency as the monitors, activated vBlank sync also from nVidia panel, still nothing.. And since when only 1 monitor is enabled playback is great, it's not compiz fault or anything.. 

my PC setup is: 
intel Dual Core Quad 2,66Hz
4GB RAM at 667Hz
nVidia 9800GT


any ideas? it would be great if i could solve this problem, coz its a pain having to disable-enable the one monitor whenever i want to see a movie..!
        Thanks in advance!!:)

---

### Post by HappyFeet on 2009-09-29
Turn off compiz and do
```
sudo nvidia-settings
```
set up twinview again and see what happens.

---

### Post by Judo on 2009-09-29
That artifact is known as tearing.  I tried for a month to find a fix for it, but I found nothing. We can only hope the driver developers fix this in the future.

I've given up on TwinView and use Xinerama now.  No more tearing.

---

### Post by mocha on 2009-09-29
You have to use environment variables and nvidia-settings to specify the device to sync to for OpenGL, Xv, and VDPAU.  You also need to upgrade your driver to the 185.xx or higher series.  You should also disable the composite extension in your xorg.conf file.  Start reading the linux forum at nvnews.net, it's helped me a lot in getting the most from my nvidia card.

---

### Post by dsevastakis on 2009-09-30
thanks a lot for your fast response:) i still haven't fixed it but i'll do my best.. i install the latest drivers for nvidia and i'll what else i can do! thanks again!:)

---

