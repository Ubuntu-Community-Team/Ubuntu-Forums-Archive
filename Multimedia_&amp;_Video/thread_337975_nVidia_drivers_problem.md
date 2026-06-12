---
title: "nVidia drivers problem"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by rEvolution27 on 2007-01-13
This has frustrated me to no end and I've asked on the IRC many times to no avail. 
Here's the story. When I installed beryl, my nVidia drivers stopped working. I know this because games run very slow. Now when I try to install nvidia-glx i get this error:

      Some packages could not be installed. This may mean that you have
      requested an impossible situation or if you are using the unstable
      distribution that some required packages have not yet been created
      or been moved out of Incoming.
       
      Since you only requested a single operation it is extremely likely that
      the package is simply not installable and a bug report against
      that package should be filed.
      The following information may help to resolve the situation:
 
      The following packages have unmet dependencies
        nvidia-glx: Depends: nvidia-kernel-1.0.9746
      E: Broken packages 

When I try to install nVidia-kernel-1.0.9746 it says I already have it. 
Nothing I have tried works :( I need help.

---

### Post by scrooge_74 on 2007-01-13
Did you check this site? [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by rEvolution27 on 2007-01-14
Yes.
Every guide I try involves installing nvidia-glx and i always get that error.

---

### Post by n_hendrick on 2007-01-14
have you tried to remove the drivers manually then install them using envy?
Try this:

dpkg --purge nvidia-glx

then go to this site....

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

install envy etc. should set up nvidia automatically.

---

### Post by rEvolution27 on 2007-01-14
Yes I already did that.

---

### Post by dabl on 2007-01-14
It looks like you actually do have the latest Nvidia driver installed -- if it reports -9746, that is as new as it gets.  Probably you do not want to install nvidia-glx over it -- that's bound to cause conflict.  Your games may be running slower because Beryl is pretty resource-hungry.

I've been struggling with Beryl for several days, and I have it running as stable as I'm going to get it.  The windows borders, aka "decorations", are not as stable as they should be.  Sometimes when I run xserver it comes up with borderless windows, and I have to "reload windows decorator" from the Beryl settings menu.  Even when the borders are present, there is some visible flakiness in them -- Krusader, for example, comes up with total black borders, and no visible "x" in the upper right corner.  But the "x" is there, and if I click it Krusader closes.  Firefox sometimes has a transparent top border, with only the "x" showing.  I have Kubuntu Edgy, and it may be that some KDE/Beryl issues aren't relevant to Ubuntu.

Here are the "Device" and "Screen" stanzas from my xorg.conf, in case it helps:

> Section "Device"
    Identifier     "GeNvidia 7900GS"
    Driver         "nvidia"
    BoardName      "GeForce 7900GS"
    Screen          0
    Option	   "Coolbits"   "1"
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeNvidia 7900GS"
    Monitor        "SyncMaster 1100"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024@85" "1280x1024@60" "1280x960@85" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1280x854" "1600x1200@65" "1152x768@54" "1600x1200@60" "1152x864@75" "1600x1200@75" "1024x768@43" "1600x1200@70" "1024x768@60" "1600x1200@85" "1024x768@70" "1792x1344@75" "1024x768@75" "1792x1344@60" "1024x768@85" "1856x1392@60" "832x624@75" "1856x1392@75" "800x600@60" "1920x1440@60" "800x600@85" "1920x1440@75" "800x600@75" "2048x1536@60" "800x600@72" "2048x1536@75" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection 


---

### Post by rEvolution27 on 2007-01-14
Well i did install it before, but after I installed beryl adept says nvidia-glx is not installed and i can't run nvidia-glx-config. Now that i re-booted, my resolution is messed up, things run even slower and beryl causes kde to re-start. I think i may have to re-intall kubuntu if things keep going this way. I really don't know what do do :S

---

### Post by dabl on 2007-01-14
Can you run the Nvidia driver X server utility from Kmenu>System? If so, you can do some monitor resolution adjustments in that utility and save them.  You can also save the configuration into your xorg.conf file.  I would not think it necessary or helpful to re-install all of Kubuntu just to get your video card and monitor functioning correctly.  If you have the red Beryl icon on your taskbar, can you use the "Select Window Manager" item, change it to KDE, and then click the next higher menu item called "Reload Window Manager"?  At the worst, you could go to System>KPackage Manager, find Beryl, and have it removed.  That should take you back to pure KDE.

---

