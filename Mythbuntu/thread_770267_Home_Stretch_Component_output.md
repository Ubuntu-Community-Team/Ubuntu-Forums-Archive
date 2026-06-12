---
title: "Home Stretch: Component output"
date: 2008-04-27
forum: Mythbuntu
---

### Post by dsbw on 2008-04-27
I've got two issues left before I attain Nirvana with my MythTV box. Thanks to all the help I've received here and I hope to return that in the future. (This details my first problem.)

I want to take output from my DVI-I card and plug it into my component TV. I have a cable that will do it but the picture is hash. 

Ideally, I should be able to crank it up to 1080i but right now I'd be happy with 720x480. Actually, ideally, I should be able to switch it between 720x480 and 1920x1080, right? So far I haven't been able to achieve any change in the output.

I'm using a mobo with onboard graphics (MSI K9NGM3) but also a graphics card (because the mobo has no analog out and my TV has no digital in). I've seen a couple of recommendations to disable the onboard video but there doesn't seem to be an option for that in the bios. 

The S-Video, which is on the card, works. The TV is properly detected by the Nvidia driver and I can set the output resolution. If I plug in the DVI-I to component, on the other hand, it thinks its a generic CRT and gives me 800x600 or 640x480.

I guess I'm supposed to add modelines to xorg.config?

Right now, I have this (with only the monitor plugged in):

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection

```

Hell, I'm not entirely clear how it knows to use the VGA. I can't just unplug the monitor and plug in the TV (I'm pretty sure I've tried that). That's what I'd like to do, and it seems to work if I do that with the S-video.

This is what it says about the video card (presumably the on-board one):

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
EndSection

```

So, I'm looking for where to start to make this work.

---

### Post by Tom Mann on 2008-04-28
Taken from [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-h.html]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-h.html")

Should help you sort your TV Card woes out, otherwise you could try 
sudo apt-get install nvidia-settings
nvidia-settings

and try to detect your TV in the display configuration.
sorry I can't be much more help...

---

### Post by dsbw on 2008-04-28
> **Tom Mann said:**
> Taken from [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-h.html]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-h.html")

Should help you sort your TV Card woes out, otherwise you could try 
sudo apt-get install nvidia-settings
nvidia-settings

and try to detect your TV in the display configuration.
sorry I can't be much more help...

It detects the TV, it just calls it general CRT.

I'm kind of impressed it detects the TV at all....

I'll try that appendix. Otherwise I guess I'm stuck with S-Video. :-( And the real problem there is that if I use the S-Video out, I can't use Component 1 which is where I keep my Wii.

---

