---
title: "How do you check whether a video card is broken or is it just the setup that's wrong?"
date: 2010-08-14
forum: Multimedia Software
---

### Post by shlape on 2010-08-14
I have a GeForce 8600M GS card in a Dell Vostro 1710, which has appeared to be playing up lately, but I'm unsure whether it's the hardware itself or have I not properly set things up.

I have Ubuntu 10.04 installed with compiz, and 'rotate cube' enabled. The 'deformation' is set to cylinder. I recently tried using rss-glx (really slick screensaver) when the slow-down and screen freezes happened.

**The symptoms:**

Odd behaviour begins after attempting to log in after the screensaver has blanked the screen, i.e. screensaver ran for a while then the screen blanked. When logged back in, a 'cylinder' rotate freezes and the screen does not refresh. Clicking around the screen refreshes it somewhat. Switching between screens becomes next to impossible and a restart is required.

In general rotating the cube is OK, rotating the cylinder seems a task on the video card and rotating the sphere is horribly slow.


**Things done so far:**

Each time I log in, I need to open the NVidia settings and change the powermizer to 'prefer maximum performance'. On next reboot I will try this in xorg.conf:

```
Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
```

...as a means to have this powermiser setting fixed to maximum, but this is not the key concern.

Other settings in xorg.conf are:
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        Option          "AllowGLXWithComposite" "True"
        Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```


My questions are:
- How can I verify the card is working correctly, enough to be able to decide whether it's hardware or software at fault?
- If the hardware is proven to be OK, what am I then leaving out?

---

### Post by shlape on 2010-08-15
... just as an update, the following didn't work (in xorg.conf).

```
Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
```

The NVidia option is still set to Adaptive by default.

Meanwhile I've uninstalled rss-glx as it make my system unstable at times. Has anyone heard of problems with rss-glx? Otherwise, I'd like to hear from someone about how I can test my video card to see if that's where the problem lies.

---

### Post by shlape on 2010-08-17
* bump *

---

### Post by shlape on 2010-08-21
** bump **

---

### Post by cchhrriiss121212 on 2010-08-21
So do you still have problems after removing rss-glx? If so what are they, as the issues seem directly related to that screensaver.

---

### Post by shlape on 2010-08-21
The basic compiz functionality works ok after removing rss-glx and initially I thought the screen saver was at fault. I have another laptop with the i915 Intel GMA, which also has rss-glx and runs without any problems. The only difference is the i915 laptop uses a 64bit version of lucid. No problems there.

The nvidia driver installed through the System > Hardware Drivers facility appeared to cuase another problem where cube rotation was slow and jittery. I manually installed the latest nvidia driver from their website and this problem doesn't happen anymore.

I tried the [Unigine Heaven benchmark demo]("http://unigine.com/products/heaven/") without luck. I don't know if their software demo has problems, but I couldn't get better than about 3fps. Extremely slow and jittery. This demo eventually locks up my system.

---

