---
title: "Screen divided to three parts, when playing a movie"
date: 2009-12-27
forum: Multimedia Software
---

### Post by valexi on 2009-12-27
When I am playing a movie, it seems that some codec or something flickers the image. Sometimes I see, when they get somehow out of sync and I see the lines, where they are.
 
This happens with XBMC and also with MPlayer. What could cause this? I'll try to add screenshots later.
 
CPU: Intel C2D E6400
GPU: GeForce 9400 GT
2GT RAM, 800mhz
 
These shouldn't be the bottleneck, when playing 1080p mkv files?
 
I'm using Karmic 9.10 and latest NVIDIA drivers.

---

### Post by valexi on 2009-12-29
I have tried to take a screenshot from it, but when this error appears and I stop the image, the error is gone.
 
Could this be a problem with 24p movies TV's refresh rate missmatch? I have ubuntu set on 1080p/24hz resolution, but this doesn't seem to affect on XBMC nor MPlayer.
 
Any clues?

---

### Post by valexi on 2009-12-31
Now I managed to record this thru digital camera. Here is the video:

[http://tinypic.com/player.php?v=2946o2q&s=6](http://tinypic.com/player.php?v=2946o2q&s=6)

---

### Post by valexi on 2009-12-31
I GOT IT WORKING! This error is called "Video Tearing" and this is how I fixed it:

Edit /etc/rc.local file:

```
sudo nano /etc/rc.local
```Add this before part: "exit 0":

```
chmod 666 /dev/nvidia* &
```Then edit xorg.conf

```
sudo nano /etc/X11/xorg.conf
```Add these lines there. DRI is for Direct Rendering:

```
Section "DRI"
    Mode 0666
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
Load "dbe"
EndSection
```Then open NVIDIA settings: System -> Administration -> NVIDIA X Server Settings:
X Server XVideo Settings -> Check box for Sync to VBlank
OpenGL Settings -> Check box for Sync to VBlank

Then Quit NVIDIA Settings and reboot Linux. If you still see Tearing try this:

System -> Preferences -> Appearance
Open Tab: Visual Effects
And check: None


This fixed Video Tearing problems for me!

---

