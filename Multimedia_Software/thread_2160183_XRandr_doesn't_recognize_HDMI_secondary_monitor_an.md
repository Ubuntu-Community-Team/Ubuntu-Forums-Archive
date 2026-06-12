---
title: "XRandr doesn't recognize HDMI secondary monitor and all HDMIs read as DVI."
date: 2013-07-05
forum: Multimedia Software
---

### Post by theShaggy on 2013-07-05
Hi all,

I have a Nvidia GTX650 with dual screens - a DVI output going to a BenQ monitor and an HDMI output going to an LG LCD TV.

When I open Nvidia-settings, I see both of them, can rearrange them and everything seems to functioning properly. In Kubuntu, I even get the "New Activity" button in the corner, and it will bring up the banner along the bottom to select a new activity. The thing is, I don't get this in Unity, and going to Display and Monitor brings up nothing.

XrandR outputs the following:

```
shaggy@MANTRID:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+   59.9     50.0     30.0     30.0     25.0  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9     50.0  
   1152x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x576        50.0     25.0  
   720x480        59.9     30.0  
   640x480        75.0     59.9     59.9  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
```

Note that only one display is active, and there is no HDMI-0 available - it's all DVI.

I'm confused because I can't get it to recognize the HDMI (this also applies to audio out - I try setting audio to work on the TV and it just plays nothing), nor can I get windows to go there. Have I missed something? Do I need to activate it on XRandR to work? I've been reading on that, but I am still unsure what to do in this context.

Help! Getting video and games running on the TV is one of the last things I need to mostly switch back from Windows! 

(Ubuntu 13.04 - I've tried KDE and Unity)

---

### Post by theShaggy on 2013-07-05
I update -

It looks like Kubuntu works. I'm not able to move programs between windows (I don't need to drag and never did, but it'd be nice to be able to send a window to another screen), and I can't get HDMI audio out to work.

---

