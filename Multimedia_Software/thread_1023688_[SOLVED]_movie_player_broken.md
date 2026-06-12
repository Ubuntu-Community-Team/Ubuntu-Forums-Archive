---
title: "[SOLVED] movie player broken"
date: 2008-12-28
forum: Multimedia Software
---

### Post by frost151n on 2008-12-28
hello,
umm.. when ever i play a movie or music the video or visualization flashes, continuously.
Its very irritating!!!
Please help.

---

### Post by xc3RnbFO8P on 2008-12-28
Does it only happens in Movie Player (Totem)?

---

### Post by frost151n on 2008-12-28
Nope, Rhythmbox Music Player as well. I don't have anything else.
It just got worse!!!

---

### Post by xc3RnbFO8P on 2008-12-28
What video card do you have?

---

### Post by linux_tech on 2008-12-28
Some decent video players are:
VLC
Banshee

You may also want to try
beep-media-player

There are alot of good recommendations here as well-
[http://www.ubuntugeek.com/ubuntu-media-players-overview.html](http://www.ubuntugeek.com/ubuntu-media-players-overview.html)

---

### Post by frost151n on 2008-12-29
Ringi- I have an ATI HD 3850 512MB, Sapphire make. 
linux_tech- I'll try other players, see what happenes.

---

### Post by xc3RnbFO8P on 2008-12-29
Here is four possible solution:
> Disable Compiz, System> Preferences> Appearances> Visual Effects> None 
> Type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).
> May be the vertical synchronization is disabled from the graphics drivers, I am new to linux and can only tell that it is most probably a VSYNC issue. The video will look cutting or tearing effects. VSYNC is the synchronization of bringing down the frame rate of the video to monitor refresh rate level like 60 fps or 75 fps. If you turn VSYNC to 'ON' the video will no longer flicker.
> I edited my xorg.conf file to include this:
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
and it works beautifully now. i only need to turn off compiz when i go to fullscreen. totem looks great - so much better placy on totem than vlc. whereas before i did this totem was ALWAYS choppy.

---

### Post by frost151n on 2008-12-30
Thnx a lot Ringi. The second one worked for me.
Well so did the first but who want's to disable effects everytime they want to watch a video!!!
...thnx again.

---

