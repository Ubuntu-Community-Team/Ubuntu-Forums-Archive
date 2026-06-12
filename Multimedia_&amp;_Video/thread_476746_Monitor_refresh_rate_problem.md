---
title: "Monitor refresh rate problem"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by cogadh on 2007-06-17
I don't know when or how this problem started, but I now have had the same issue twice, and this time it is occurring on a clean, fresh install of Feisty. Basically, my monitor will only do minimal refresh rates:
50 Hz or 53-56 Hz @ 1024x768
51 Hz or 59-63 Hz @ 800x600
52 Hz or 68-71 Hz @ 640x480
*EDIT - This is what the System > Preferences > Screen Resolution tool reports, if I use the monitor's built-in functions, it appears that I am running at 85 Hz. However, the problem with Ubuntu misreporting the refresh rate is affecting other applications, specifically games.*

The monitor should max out at 85 Hz both on 1024x768 and 800x600 and shouldn't be able to go below 60 Hz @ 1024x768.

The only changes I have made to this install of Feisty is I installed the nvidia-glx-new package for my GeForce FX 5200 by following the instructions [here]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html"). I also modified my xorg.conf to include the proper monitor sync and refresh rates (yes I am sure they are correct). The monitor is connected to the PC via a KVM switch, though I don't see how that could cause the problem. 

I believe the problem must have something to do with how I configured my xorg.conf, but I don't see where I went wrong. Please see the relevant excerpts below and any help would be greatly appreciated.
```
Section "Monitor"
    Identifier     "SyncMaster"
    HorizSync	   30-70
    VertRefresh    50-160
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "SyncMaster"
    Option 	   "AllowGLXWithComposite" "true"
    Option 	   "AddARGBGLXVisuals" "true"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by logos34 on 2007-06-17
What about 

$ nvidia-settings

Can't yu choose 75 or 85Hz there and apply?

---

### Post by cogadh on 2007-06-17
See, I knew all I needed was a gentle shove in the right direction. :)

I was able to set 85 Hz as the refresh rate in the nvidia-settings tool. Interestingly, the Gnome tool now reports my refresh rate as 96 Hz. I'm beginning to think that I can't trust that tool at all.

---

### Post by logos34 on 2007-06-17
> Interestingly, the Gnome tool now reports my refresh rate as 96 Hz. I'm beginning to think that I can't trust that tool at all.

Agreed.  Mine too.  But I just ignore it (it's set for 85Hz but gnome screen res. says '1024x768@130Hz'! Just blows it's mind...)

---

### Post by cogadh on 2007-06-18
Okay, I was ready to let this one go and just consider it a quirk of Ubuntu, but not anymore.

I just did a re-format/re-install of Ubuntu on the same machine. This time I paid attention to when the error started to happen. It occurs immediately after installing and configuring the nVidia driver. So far, I've managed to duplicate the problem with both the "nvidia-glx-new" package and the latest install .run from nVidia (I reformatted between each install). Now I'm concerned that this may be a problem with the current nVidia driver. Even though I can now set the refresh rate properly, I'm still have resolution problems with 3D games.

Before I run another re-format/re-install, has anyone experienced this problem using the plain "nvidia-glx" package?

---

### Post by cogadh on 2007-06-18
If you're interested, I found a Launchpad bug on this with a fix for this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105/comments/9)

Adding the fix totally corrected the refresh rates for me.

---

### Post by logos34 on 2007-06-18
> **cogadh said:**
> If you're interested, I found a Launchpad bug on this with a fix for this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105/comments/9)

Adding the fix totally corrected the refresh rates for me.

TThanks for the tip.  It was never a high priority for me so I just blew it off.  But it would be nice to have it working correctly.  

I don't see 'dynamicTwinView" listed on my xorg.conf.  I  perused the nvidia readme and appendix, and this is what I came up with:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
**    Option        "DynamicTwinView" "false"**
EndSection

Is that what your's is like? Or does it go under 'Screen' section?

---

### Post by cogadh on 2007-06-18
It can go either under Device or Screen, it works in both places.

---

### Post by logos34 on 2007-06-18
Ok, tried it in both places.  Works, but it disables X server config option in nvidia-settings (!)  I actually prefer the latter--has a few more options.   I am not a gamer, but the next time I run any high-end 3-D apps I'll make sure to insert the option.

---

