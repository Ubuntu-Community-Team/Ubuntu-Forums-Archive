---
title: "Nvidia + TV-Out"
date: 2010-06-07
forum: Multimedia Software
---

### Post by curioususer on 2010-06-07
I have an NVIDIA 9500 GT.  I've installed the proprietary drivers (v. 195).  I am running Karmic Koala (9.10).

I cannot figure out how to get tv-out working.  Here is my x.org:
--------------------------------------------------------------------------------------
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
--------------------------------------------------------------------------------------
Everything else seems to be working.

The card uses s-video out.  I don't see any other devices listed when I run nvidia-settings.

What to do?

---

### Post by jocko on 2010-06-07
Try adding this to your xorg.conf (either in the "Device" section or the "Screen" section):
```
Option "ConnectedMonitor" "DFP, TV"
```
Or:
```
Option "ConnectedMonitor" "CRT, TV"
```

DFP is if you connect your monitor via a DVI cable, CRT if it's connected via a VGA cable (even if the display is not really a cathode ray tube). Not sure how it will work if you leave out the normal monitor and just use "TV".

---

### Post by curioususer on 2010-06-07
That doesn't work for me, though it does create an entry for "TV" in nvidia-settings (that can't be edited).

---

### Post by jocko on 2010-06-07
Weird. What happens if you boot your computer with only the TV connected?
Do you connect to an s-video input on your TV, or do you use an s-video to scart or rgb adapter?

---

### Post by curioususer on 2010-06-07
I have an s-video input on the tv.

---

### Post by curioususer on 2010-06-07
[http://ubuntuforums.org/showthread.php?p=4929055#post4929055](http://ubuntuforums.org/showthread.php?p=4929055#post4929055)

It looks like people can come close if they edit x.org manually and hope for the best.  Seems like this is one of those things Ubuntu can't quite handle yet.

---

### Post by jocko on 2010-06-07
Again, what happens if you boot your computer with only the TV connected?

I had an old ati card that refused to initialize TV-out if a monitor was connected to the DVI port. The only way to get both TV-out and DVI to work was to unplug the monitor and reboot the computer to let the video bios on the graphics card initialize TV-out. Then I could pause boot by bringing up the grub menu and plug the monitor back in before I let it continue booting.

Otherwise: Try a different s-video cable.

---

### Post by curioususer on 2010-06-07
Weird, that worked.  I wonder why?  It seems so counter intuitive.

For people happening onto this thread in a similar situation, the steps that worked were:

Turn off computer.
Unplug Monitor.
Plug in S-Video.
Turn on TV.
Reboot.
Verify TV is working.
Turn off computer.
Plug in Monitor.
Reboot.
Verify both are working.

The controls are a bit wonky, and the quality is crap unless I'm watching video, but its functional for what I want it for.

Thanks!!!

---

### Post by jocko on 2010-06-07
> **curioususer said:**
> ... the quality is crap unless I'm watching video, but its functional for what I want it for.
Try adding this to the "Screen" section of your xorg.conf:
```
Option   "TVStandard" "PAL-B"
Option   "TVOutFormat" "SVIDEO"

```This will switch the TV standard to PAL-B (change this to whatever standard is used in your country. If you are not sure which TV standard your TV uses, check on [this]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-h.html") page).
It will also force the output to S-video instead of composite.
Setting the TV standard or output format wrong usually results in weird colors (or no color) and a flickering image.
> **curioususer said:**
> 
Thanks!!!
You're welcome.

---

