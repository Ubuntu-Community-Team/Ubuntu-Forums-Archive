---
title: "ubuntu 9.04 jerky movies"
date: 2009-05-03
forum: Multimedia Software
---

### Post by ddalcu on 2009-05-03
I've done a clean install of ubuntu 9.04 i386 and when I play any HDTV movies (not FullHD, just 720p) some sequences where is a lot of movement are jerky. This didn't happen on ubuntu 8.04 LTS... How can I solve this problem?

Thanks!

CPU: AMD 64x2, 2200MHz
Vide: GForce 8800 GT
Mem: 4G

---

### Post by ddalcu on 2009-05-03
please, any help?

---

### Post by xc3RnbFO8P on 2009-05-03
Did you install restricted driver in System> Administration> Hardware Drivers ?

---

### Post by ddalcu on 2009-05-03
sure, I've installed "*NVIDIA accelerated graphics driver (version 180)*"

---

### Post by xc3RnbFO8P on 2009-05-03
Check this:

> * GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer 
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.

---

### Post by ddalcu on 2009-05-04
None of the above worked...
I somehow managed to partially solve the problem by downgrading the video driver from  version 180 to 173... It's a little better, but there are still problems...

---

### Post by hotani on 2009-05-12
There are problems with the nvidia-glx driver 180.44. I had to drop back to 8.10 because of having to hard boot my system a couple of times a day. 

I'm attempting to view HD video on an ATI system at home and none of the above methods utilize the video card. When I choose "openGL" in VLC, the video is blocky because of a bug in VLC 0.9.9. Gstreamer won't even play fullscreen (drops so many frames the picture moves about one frame a second), Mplayer either crashes when I attempt to open a video or plays about as smoothly as totem - a frame or two a second.

This is using the latest fglrx driver and an HD3200 video card which is more than capable of playing full HD video. 

Right now my best option is to set VLC to use X11 which processes everything with the CPU. My CPU monitor is maxed out while playing HD video, but it will play somewhat smoothly.

---

### Post by lvleph on 2009-05-12
If you have compiz running it is something probably cpu usage. I had to just turn compiz off.

---

### Post by ddalcu on 2009-05-12
I've managed to solve the problem finally. I've reinstalled the video driver from nvidia (I'm sure that it also works with the 180 version driver that ubuntu provide) and I've installed the last version of mplayer. The one that ubuntu provide is very old and it will not work with that. After that, in mplayer I use **vdpau** as output driver (**-vo vdpau**) and **-vc ffmpeg12vdpau,ffh264vdpau,**. Using this output, witch from what I've heard is only available from nvidia 8000 series up, releases the main CPU and gives the movie processing to the video card CPU. I'm sure that windows is doing the same thing (in windows all hdtv, even 1080p works smooth) because after I've changed my video card from 6600GT to 8800GT I've managed to watch hdtv movies, the main CPU remaining the same. I think that one should have a very powerful CPU to watch full hd movies only with that.
Good luck!

---

